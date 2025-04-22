---
alias: Firefox
---

# Firefox

Cross platform open source web browser

- [bookmarklet-service-now-ticket-markdown-link](../../../services/service-now/bookmarklet-service-now-ticket-markdown-link.md)

## General

Important data you want to preserve:

- bookmarks
- passwords
- add-ons
- extensions
- extension data

**Password sync makes phone login easier!**

Syncing passwords between workstation and phone eliminates hassle of typing passwords on the phone.

- **Send page/link to device**: Open in Firefox on phone or computer

## Config

### about:config

- `network.protocol-handler.export-all: false`: _Review this_ This tried to open bittorrent magnet links in the browser

## Hotkeys

**Ctrl + Shift + B**: Toggle bookmark toolbar (good for screenshots that show URL and page body)

## Dev Tools

`-status-code:200`: Filter out 200s from network pane.

## Profile manager

- [profile manager](https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles)

You may want to keep a different profile for personal / work.

When firefox is open: `about:profiles`

When firefox is closed: `firefox -P` (or `firefox -ProfileManager`)

Profiles live in: `~/.mozilla/firefox/profiles.ini`

## Assigning containers to bookmarks

Sometimes you have sites you want to open across different containers (e.g.
Outlook) and it's a pain to do "Container on bookmark dropdown menu" every
time.

If you have the Firefox plugin ["Open external links in a
container"](https://addons.mozilla.org/en-US/firefox/addon/open-url-in-container/)
installed you can assign bookmarks to containers by putting the following in the
URL field for a bookmark:

<!-- markdown-link-check-disable-next-line -->

ext+container:name=Personal&url=https://outlook.office.com/mail/inbox

Where `container:name` is the name of your container and `url` is the URL you
wish to open.

With this approach you can have multiple bookmarks for the same site with each
opening in a different container.

## Don't close window when last tab closed

I don't want to have to keep typing in my Primary Password to unlock password manager.

- Type "about:config" in the address bar
- Accept the warning message
- Search for "browser.tabs.closeWindowWithLastTab"
- Double-click to set it to "false"

## Troubleshooting

### Troubleshoot mode

- [troubleshoot mode](https://support.mozilla.org/en-US/kb/diagnose-firefox-issues-using-troubleshoot-mode)

**Troubleshoot Mode** runs Firefox with some features and customizations disabled ([see below](https://support.mozilla.org/en-US/kb/diagnose-firefox-issues-using-troubleshoot-mode#w_what-does-troubleshoot-mode-disable) for details). If you're having a problem in Firefox that does not occur in Troubleshoot Mode, the cause of the problem is one of the disabled items.

### Refresh Firefox

If you're having problems with Firefox, refreshing may help by restoring the browser to its default state while saving your essential information, like bookmarks and passwords.

- [refresh firefox](https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings)

#### Firefox will save these items:

- Bookmarks
- Browsing and download history
- Passwords
- Cookies
- Web form auto-fill information
- Personal dictionary

#### These items and settings will be removed:

- [Extensions and themes](https://support.mozilla.org/en-US/kb/find-and-install-add-ons-add-features-to-firefox)
- Website permissions
- Modified preferences
- [Added search engines](https://support.mozilla.org/en-US/kb/add-or-remove-search-engine-firefox#w_add-a-search-engine)
- DOM storage
- [Security certificate](https://support.mozilla.org/en-US/kb/secure-website-certificate) and device settings
- [Download actions](https://support.mozilla.org/en-US/kb/change-firefox-behavior-when-open-file)
- [Toolbar customizations](https://support.mozilla.org/en-US/kb/customize-firefox-controls-buttons-and-toolbars)
- User styles (chrome subfolder containing userChrome and/or userContent [CSS files](https://wikipedia.org/wiki/Cascading_Style_Sheets), if previously created.)
