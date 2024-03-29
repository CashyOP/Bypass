Debloated fork of *bypass-all-shortlinks*.

Automatically bypass many link shorteners [(supported_sites.txt)](https://codeberg.org/Amm0ni4/bypass-all-shortlinks-debloated/src/branch/main/supported_sites.txt)

## Install
**Install with [this link](https://codeberg.org/Amm0ni4/bypass-all-shortlinks-debloated/raw/branch/main/Bypass_All_Shortlinks.user.js)**

(you need a userscript manager like [ViolentMonkey](https://violentmonkey.github.io/) installed in your web browser)

## Improvements in this fork
- **No loading the script indiscriminately on every site.** The script will be loaded only for the sites that are supported. (the original userscript is loaded in every site you visit which is not necessary).
    - _Note: I have removed as supported sites:
        - Youtube `*://*.youtube.com/shorts/*`_(@match)_ (which is used for redirecting shorts)
        - Google: 
            - Drive/Docs `/^(https?:\/\/)(drive|docs)\.google\.com(\/.*)/`_(@include)_ (which is used for Auto-DL from Drive/Docs)
            - redirects `/^https?:\/\/(?:www\.)?google\.com\/url.*[?&]q=/`_(@include)_ (used for bypassing these redirects) 
            - Recaptcha `*://*/recaptcha/api2/*`_(@match)_ or `/^(?:https?:\/\/)?(?:www\.)?(?:google\.com|recaptcha\.net)\/recaptcha\/api2\/.*$/`_(@include)_ (used for Auto-Open of captchas in many sites).

        Not including these is to prevent some people from worrying about the script running on sensitive sites. These sites can be enabled manually in your userscript manager using those mentioned regular expressions in the script settings.
- **No useless added redirects.** The script will not redirect to 'rotator.nurul-huda.sch.id' or 'free4u.nurul-huda.or.id' before your destination URL, which are intermediary sites set by the developer for tracking / [collecting analytics](https://i.ibb.co/D1zYG1v/topcountry17-04-2023.jpg) and showing ads.
- **No injecting unnecesary tracking in every site**. 
    - The script will not inject the an iframe for tracking.
    - The script will not inject this weird _"adcopy_response"_.
- Removed all the non-english languages to avoid buggy text characters.

Original script by *bloggerpemula*: [greasyfork.org/scripts/431691](https://greasyfork.org/scripts/431691)

## How I modify the original userscript
Executing these 3 python scripts in order:
- 1_download_untouched.py
- 2_generate_includes.py
- 3_patch.py
