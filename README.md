# cordova-build-bundle-release and sign then compress it
#how to build android app using cordova and sign release 
#to create a release go to your project/platforms/android folder in CMD and enter this code
`gradlew bundelRelease`
#then create a key to sign your build by entering this command and follow steps>
`keytool -genkey -v -keystore myKey.keystore -alias myKeyAlias -keyalg RSA -keysize 2048 -validity 10000`
 #this command generated file named myKey.keystore Keep in in safe place for further updates and now lets sign our bundle.aab
# copy your generated platforms/android/app/build/output/bundle/app.aab to main project directory (it means myKey.keystore and apk file in the same folder)
# then go to this folder "which contains keystore and aab file" in cmd and run this command to sign apk
`jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore myKey.keystore app.aab myKeyAlias`
# now compress signed file and upload it to google play store
`zipalign -v 4 app.aab signedandcompressed.aab`
