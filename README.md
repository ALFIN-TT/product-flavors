# product-flavors
Demo app for add multiple product flavours
 
 Product flavor is a variant of your app. It is very useful when you want to create multiple versions of your app.


## Setting Up Product Flavors
Open up your ```build.gradle``` file in the app module and add your flavors inside the android section.
The below example has 3 product flavors added with each having its own ```applicationId```, ```signingConfig```

```
 flavorDimensions 'flavours'
    productFlavors {
        flavor1 {
            dimension 'flavours'
            applicationId 'com.example.productflavours1'
            versionCode 1
            versionName '1.0.0'
            signingConfig signingConfigs.signKey1Config//specify sign key here
            resValue "string", "resvalue1", "valueFromGradle1"//create resource value from here.
            buildConfigField 'int', FIELD_NAME_BUILD_CONFIG_FIELD, "1"//create build config field
        }

        flavor2 {
            dimension 'flavours'
            applicationId 'com.example.productflavours2'
            versionCode 1
            versionName '1.0.0'
            signingConfig signingConfigs.signKey2Config//specify sign key here
        }

        flavor3 {
            dimension 'flavours'
            applicationId 'com.example.productflavours3'
            versionCode 1
            versionName '1.0.0'
            signingConfig signingConfigs.debug//specify sign key here.
        }
    }
```
Select Build > Select Build Variant in the menu bar, and you will see the different Build Variants auto-generated when you added the Product flavors.

![Select Build variant and product flavour](https://user-images.githubusercontent.com/58541387/199710606-4f092a25-93e7-474d-b4de-944b006f37d8.png)

## Structuring your Flavors
Your main folder is the one that contains all the common and shared code between flavors, you can create flavor specific code and files by creating different source set for each flavor MyProject/app/src/main

![Add multiple google-services json files based on the flavour](https://user-images.githubusercontent.com/58541387/199712077-b8be7639-0bdc-4d36-996a-e8b3606988a6.png)

## Get the flavor at runtime
You can check direct with flavor and your config name in everwhere, BuildConfig has already BuildType

![Accessing  BuildConfig Fields and Flavours](https://user-images.githubusercontent.com/58541387/199715175-8907f8cd-3831-499f-a9a5-460829e11be7.png)

```
if(BuildConfig.BUILD_TYPE == "release"){// TODO}
else if(BuildConfig.BUILD_TYPE == "staging"){ //TODO }
else if(BuildConfig.BUILD_TYPE == "debug"){ //TODO }
```
