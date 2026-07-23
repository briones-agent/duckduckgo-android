# DuckDuckGo Android + React Native

This is an experimental fork of the official [DuckDuckGo Android](https://github.com/duckduckgo/Android) with the sole purpose of testing brownfield support for Expo and React Native in large native-first codebases. Its commits serve as a reference for anyone interested in integrating React Native into an existing Android app, especially those that don't want to refactor the whole project structure to accommodate React Native.

This project uses Expo's brownfield isolated approach, consuming a prebuilt **fused AAR** (a single artifact bundling the brownfield library, all autolinked Expo/React Native modules, and the release JS bundle) from a remote Maven repository — no local React Native toolchain is required to build this fork.

## Integration steps

Check commits for detailed steps, full instructions can be found in the [expo-brownfield documentation](https://docs.expo.dev/brownfield/overview/). The fused AAR is built with `npx expo-brownfield build:android --fused` from the Expo app in [briones-agent/packages](https://github.com/briones-agent/packages) and published there as a static Maven repository.

1. **Add the Maven repository**: In the root `build.gradle`, add `https://raw.githubusercontent.com/briones-agent/packages/main/maven` to `allprojects.repositories`.
2. **Add the dependency**: `implementation 'dev.expo.brownfield:expobrownfield-fused-release:1.0.1'` in `app/build.gradle`.
3. **Add React Native view**: Subclass `dev.expo.brownfield.BrownfieldActivity` (shipped inside the AAR), call `showReactNativeFragment()`, register the activity in the manifest, and launch it from an "Expo" entry in the browser's bottom-sheet menu.

<details>
<summary>DuckDuckGo Android</summary>

# DuckDuckGo Android

Welcome to our android application. We are excited to engage the community in development, see [CONTRIBUTING.md](CONTRIBUTING.md).

## We are hiring!
DuckDuckGo is growing fast and we continue to expand our fully distributed team. We embrace diverse perspectives, and seek out passionate, self-motivated people, committed to our shared vision of raising the standard of trust online. If you are a senior software engineer capable in either iOS or Android, visit our [careers](https://duckduckgo.com/hiring/#open) page to find out more about our openings!

## Building the Project
We use git submodules and so when you are checking out the app, you'll need to ensure the submodules are initialized properly. You can use the `--recursive` flag when cloning the project to do this.

    git clone --recursive https://github.com/duckduckgo/android.git

Alternatively, if you already have the project checked out, you can initialize the submodules manually.

    git submodule update --init
    
## Terminology

We have taken steps to update our terminology and remove words with problematic racial connotations, most notably the change to `main` branches, `allow lists`, and `blocklists`. Closed issues or PRs may contain deprecated terminology that should not be used going forward.

## Contribute

Please refer to [contributing](CONTRIBUTING.md).

## Discuss

Contact us at https://duckduckgo.com/feedback if you have feedback, questions or want to chat. You can also use the feedback form embedded within our Mobile App - to do so please navigate to Settings and select "Leave Feedback".

## License
DuckDuckGo android is distributed under the Apache 2.0 [license](LICENSE).

</details>
