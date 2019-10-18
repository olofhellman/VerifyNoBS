# VerifyNoBS (Build Settings)

This script is meant to be called from an Xcode run script build phase.
It verifies there are no buildSettings embedded in the Xcode project as it is preferable to have build settings specified in .xcconfig files.

## How to use:
Put this script in a folder called 'buildscripts' next to your xcode project.
Then, add a "Run Script Build Phase" to one of your targets with this as the script

    xcrun -sdk macosx swift buildscripts/VerifyNoBS.swift  --xcode  ${PROJECT_DIR}/${PROJECT_NAME}.xcodeproj/project.pbxproj

This will run the script and fail your build if any build settings are detected in your project file.
The `--xcode` switch will output any errors in a format that is picked up by Xcode so you can directly click on the error and jump to the offending spot in the project file.

When running it without the `--xcode` switch errors will simply be written to stderr.
