Status: DRAFT. Do not use.

PostgreSQL function for last inserted ID (based on the `sequence` from which the ID is being generated if numeric - doesn't work on derived identifiers!) :

Option 1: CURRVAL(<sequence name>);.

For example:
  
    INSERT INTO persons (lastname,firstname) VALUES ('Smith', 'John');
    SELECT currval('persons_id_seq');

Option 2: LASTVAL();

This is similar to the previous, only that you don't need to specify the sequence name: it looks for the most recent modified sequence (always inside your session, same caveat as above).

Option 3: INSERT with RETURNING

INSERT INTO persons (lastname,firstname) VALUES ('Smith', 'John') RETURNING id;


Last one is probably cleanest option.
