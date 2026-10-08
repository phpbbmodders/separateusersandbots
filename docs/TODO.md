# TODO

Ideas not yet built, practical and speculative alike.

## Hide bots from non-admins, as a setting

Fold the job of phpbbmodders/hidebots into this extension as an on/off
setting, so boards need one extension instead of two. hidebots can be
archived once this ships.

Why: both extensions rewrite the "Who is online" text through the same
event (`core.obtain_users_online_string_modify`), so with both enabled,
whichever runs last wins. One extension doing both avoids that.

Planned behavior, matching hidebots today:

- When the setting is on, bots are left out of the "Who is online" list for
  everyone except administrators, counted as hidden users instead.
- They are also left out of the full *Who is online* page
  (`core.viewonline_modify_sql`), and of the 24 Hour Activity list
  (`rmcgirr83.activity24hours.modify_active_users`) when that extension is
  installed.
- When the setting is off, behavior is exactly as it is now.

Still needs deciding:

- Where the setting goes. This extension has no ACP page; one Yes/No option
  on an existing ACP page (for example *Load settings*) avoids adding a new
  module.
- Who still sees bots: administrators only, as hidebots does, or a new
  permission.
- Moving hidebots users over: when the update installs, switch the setting
  on if hidebots is enabled, and tell the admin to disable and remove
  hidebots.
