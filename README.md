# JCAppStoreContent

This is only a card applet storage, parsed by JCAppStore. There are applet cap files, language packs, graphics and additional info stored so that the content is transparent.


### info_[lang].json
This file is used to parse the store content. For localization, an info file must be present with `lang` tag of the language the info is translated to. For example, a czech translation would be **info_cz.json**, german **info_de.json**.

The following fields are supported
 - `type`: a string, default `applet` for the applet entity
 - `name`: a string, required, unique applet identifier, should be in lower camel case and consist of the author and instance name
 - `title`: a string, required, applet name as displayed to the user
 - `applet_instance_names`: an array of strings, default `null`, specifies custom applet names and possibly AIDs - if provided the store fills in the new applet AID upon the installation - let's say we have a cap file with one applet instance: 1122334455. We want the applet title to be different from `title` field: `['My Applet']`; in case we want the applet to be installed with different AID, we must use '0x' to tell the parser we are going to provide AID values as well: `['0x', 'My Applet', F120BAC10998AA0100001]`; all instances of the `cap` file must be specified; `0x` can be only as the first element - in that case, all applets must also define custom AID
 - `icon`: a string, default `""`, a name of the image to associate with the applet, must be present in the `Resources` folder
 - `latest`: a string, required, the latest version available
 - `versions`: an array of strings, required non-empty, a list of available versions, prefferably sorted - latest as the last one
 - `builds`: a json object, definition of the SDK verions for each version: all versions must have at least one SDK defined in `version: [nonempty array of strings of SDK versions]` form
 - `author`: a string, required
 - `description`: a string, required, HTML - styled description of the applet
 - `url`: a json object, at least one child required: the form is `name: string url`, for example `"Repository": "https://github.com/petrs/JCAppStoreContent/"`.
 - `usage`: a string, required, HTML - styled use swift guide - should at least give stop-by-step installation process and include tutorials if no tutorials are provided in the `url`
 - `keys`: a boolean, default `false`, whether the applet include any sensitive data that will be lost upon deletion (e.g. private keys)
 - `default_selected`: a string, default `""`, AID of the applet to make as deafult selected (original AID, not custom)
 - `pgp`: a string, default `""`, a key fingerprint the custom signature was made with
 - `signed_by`: a string, default `""`, a signature author's name, the file with detached signature will be searched for as `[cap file name].cap.[value provided here].sig`
 
 
