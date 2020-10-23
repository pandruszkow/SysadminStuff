## Minimise to tray
If you want to keep your taskbar uncluttered, you can configure Outlook to minimise to tray instead of the taskbar.

Follow these steps (Outlook 2016/365):
1. Right click Outlook tray icon
2. Make sure `Hide When Minimized` is ticked

Make sure you enable email notifications to not miss anything :)


## Single-instance mode
By default, Outlook makes it easy to open multiple windows (of your inbox, for example) at the same time. My preferred behaviour is that Outlook keeps only one window open no matter how many times it's launched.

There doesn't appear to be a corresponding option in the Outlook settings window, but there is a workaround to achieve the same effect by changing Outlook's launch arguments.

Follow these steps (Outlook 2016/365):
1. Find the shortcut(s) you use to launch Outlook. If there isn't one, create it. You can find Outlook under `C:\Program Files (x86)\Microsoft Office\root\Office16`.
2. Add the parameter `/recycle` at the end of `Target` text box in the `Shortcut` tab.
3. Save the shortcut(s).
4. Make sure that the `/recycle` parameter is present in any other shortcuts you are using. Check your `Startup` folder if you are using this to launch Outlook on startup.
5. (Optional) Update the Outlook shortcut under `All Programs -> Microsoft Office 20NN` if you have admin access.
6. (Optional) If you have Outlook pinned to your taskbar, unpin it and pin the shortcut with `/recycle`.
7. (Optional) If you have Outlook pinned to your Start Menu, remove the old shortcut and pin/move the shortcut with `/recycle` there.

(source: [Microsoft Community - Outlook 2013 recycle option for single instance?](https://answers.microsoft.com/en-us/office/forum/office_2013_release-outlook/outlook-2013-recycle-option-for-single-instance/a0cc69d1-3ae6-469f-b790-a7917e00b8c5?db=5))
