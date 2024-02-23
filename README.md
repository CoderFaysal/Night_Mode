# Night Mode Apply

## First go to Theme and set Style

theme.xml
```
    <style name="TEXT">
        <item name="android:textColor">#000000</item>
    </style>
```

theme.xml (night)
```
    <style name="TEXT">
        <item name="android:textColor">#FFFFFF</item>
    </style>
````
## XML

```
<Switch
        android:id="@+id/switch_mode"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        tools:ignore="UseSwitchCompatOrMaterialXml"
/>
```





## JAVA

First I cange mode and then i save this mode in SharedPreferences

```
Switch switch_mode;
SharedPreferences sharedPreferences;
SharedPreferences.Editor editor;
boolean nightMODE;

```

Type Code inside the onCreate Bundle 
```
switch_mode = findViewById(R.id.switch_mode);

sharedPreferences = MainActivity.this.getSharedPreferences("MODE", Context.MODE_PRIVATE);
nightMODE = sharedPreferences.getBoolean("night", false);

if (nightMODE){
        switch_mode.setChecked(true);
        AppCompatDelegate.setDefaultNightMode(AppCompatDelegate.MODE_NIGHT_YES);
}


switch_mode.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
        @Override
        public void onCheckedChanged(CompoundButton compoundButton, boolean isChecked) {

        if (nightMODE){
                AppCompatDelegate.setDefaultNightMode(AppCompatDelegate.MODE_NIGHT_NO);
                editor = sharedPreferences.edit();
                editor.putBoolean("night", false);
        } else{
                AppCompatDelegate.setDefaultNightMode(AppCompatDelegate.MODE_NIGHT_YES);
                editor = sharedPreferences.edit();
                editor.putBoolean("night", true);
        }
        editor.apply();


        }
});
```

## Demo Image

<img src="https://i.ytimg.com/vi/-qsHE3TpJqw/maxresdefault.jpg"/>

© All Right Reserved By Coder Faysal

