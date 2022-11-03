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
![Build apk choosing flavour and build varient](https://user-images.githubusercontent.com/58541387/199710469-ea6992c6-a24c-4562-bcf0-3d2698bb4702.png)
