## Report all files in an S3 bucket or prefix as CSV locally

1. Obtain a list of all files in the S3 bucket/prefix
2. Rewrite the list in the format:
```sh
aws s3api head-object --bucket <bucket name> --key <object key within bucket>; echo ","
```
3. Execute the rewritten list as a shell script and capture stdout to a file.
4. Your stdout will be nearly-valid JSON. Wrap the entire thing in square brackets to make the contents of the output into a valid JSON array.
5. Replace any `{}` empty object values (under the `Metadata` key) with a blank space or another no-op value. The next step will fail if you leave any unflattened objects in the JSON structure.
6. Run
```sh
jq -r '(map(keys) | add | unique) as $cols | map(. as $row | $cols | map($row[.])) as $rows | $cols, $rows[] | @csv' < input-file.json  >output-file.csv
```
7. The resulting CSV can be easily imported in LibreOffice Calc for browsing.

(The source for the expression in step 6 is https://stackoverflow.com/a/32965227)
