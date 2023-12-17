# PenguRun - A penguin on the flight for ÜPA

Pengu Run, a funny jump-and-run Android game, featuring our little antarctic friends.

This is meant to be:

- an additional training exercise for PGdP (IN0002 @TUM)
- a funny way of revising topics like Objects & Inheritance, Data Structures, Interfaces, Enums,
  Recursion and more
- a showcase of where Java is used
- an impulse for those who are interested to learn more about mobile app development
  <br><br>

This exercise is **not**:

- mandatory
- part of the regular tasks
- only consisting of topics already covered
- reviewed by the ÜL
- perfect codestyle or free of errors

Disclaimer: this exercise is **not** part of the topics of PGdP, Android app development is **not**
relevant for the ÜPA and way beyond the things you learn in PGdP. Nevertheless, it was designed to
be solved just with the Java knowledge you possess by now, this guide and a maybe a little bit of
researching.

It was originally written by [Jonas Wende](https://github.com/wjon-tum) for PGdP in WS 2023.

If you find errors, want to share improvements or contribute to this exercise, write me on Zulip
(internal only) or just [open an issue](https://github.com/wjon-tum/PenguRun/issues)

## Step-by-step guide to a working mobile app

If any of the following doesn't work immediately, don't worry, but ask Google. Being able to solve
technical issues by searching the internet is a skill that can save you lots of time in coding, and
on this topic, there are many beginner's tutorials on the internet.

### 1. IDE

As this project is written in Java, you could basically use any IDE or
even [Vim](https://www.vim.org/) to write the
Code. But in order to get additional tools and being able to run the app without much inconvenience,
I would recommend either
to [install the Android plugin in IntelliJ](https://www.jetbrains.com/help/idea/create-your-first-android-application.html)
or to use Google's IntelliJ based [Android Studio](https://developer.android.com/studio/install).
In any case, your IDE will need to download quite a few things, most important the Android SDK (
Software Development Kit). For the rest of these setup instructions, I will assume the use of
IntelliJ with Android Plugin or AndroidStudio.

### 2. Clone the repo

Use the built-in tools in IntelliJ (or AndroidStudio) to clone this project. You will find this
under `Git` or `VCS` menu if you are currently in a project, otherwise you will find a
button `Get from VCS` or similar in the startup dialog.

### 3. Understanding project structure

Having cloned the repo you will have to wait a little bit, while the IDE possibly will be
downloading many different
things (Android
SDK, [Gradle](https://gradle.org/), ...). **When this is finished** (you see no blue progress bar on
the
bottom of the window), you can
have a look at the project structure in the `Project`
tab on the left side.  
Don't feel overwhelmed by all these files and folders, you will only need a few.
Here I'd like to give a brief overview over the structure of the project:
(watch out for the exact name, there is e.g. a folder named `java`, and one
named `java (generated)`. We aren't interested in the generated folders here)

- `aƿƿ`: the root directory of the project
    - `manifests`: stores `AndroidManifest.xml`, the file which tells the Android system how the
      final
      app should be started, what icon is used for the app, what permissions it has etc
    - `java/de/tum/in/pgdp/pengurun` (this is a directory hirarchy, so e.g. `de` is a subdirectory
      of `java`): here are our Java files, and here **we are going to work**
        - `Solution_01`, `Solution_02`, `Solution_final`: here you can find solutions for the
          subtasks as well as for the final app
    - `res`: holds all the apps resources, especially:
        - `drawable`: contains all images used in the app
        - `layout`: contains static layout files
        - `mipmap`: contains the launcher icon, so the icon you see on your Android device when you
          have this app installed
        - `values`: contains all sorts of values (color values, strings with translations in other
          spoken languages, ...)
- `Gradle Scripts`: here are the scripts stored, according to which the IDE builds the app. They
  define things like libraries used, the Android versions your app supports, etc

### 4. Don't panic, just start coding

#todo

### 5. Run your app

#### If you have, want to use and can connect an Android device

Normally, you can't just execute commands, install apps or use a debugger on your Android phone from
a different device. To be able to install and debug your app, run the following steps:

- On your Android device, go to settings
- Find a textfield labeled `Buildnumber` under `Software information` or just search for it in the
  settings
- Tap on this textfield `Buildnumber` 10 times. You should see a message informing you that you
  unlocked developer settings
- Find these newly unlocked `developer settings` in your settings by searching for it
- If found, enable the general `developer settings`, and then scroll down until you find the
  option `USB-Debugging` and enable it
- Now connect your phone (or tablet) to your computer via cable
- You will be asked on your phone whether you want to trust the connected computer, allow this
- Now you should see your device's name in the dropdown menu in your IDE in the top bar

Should you run into problems, maybe have a
look [here](https://developer.android.com/studio/run/device).
<br><br>

#### If you haven't, don't want to use or can't connect an Android device

This is no problem, we will use an *Android virtual device*. It is basically a virtual machine,
emulating the exact behavior of a fully functional Android phone. This works best when running on a
computer with a little more resources (more RAM, faster CPU), as the computer will be running a
whole Android system in parallel. To create your virtual device, run the following steps:

- Open the `Device Manager`, to be found on the right side of the IDE
- If no device exists up to now, create a new one using the `+` button
- Select a hardware configuration according to your likes, click `next`
- Select a supported Android version (the number in the `API level` column must be between 26 and
  34, because or app will support devices from Android 8 to the current Android 14), click `next`
- Give the device a name and click `finish`
- Now you should see your virtual device's name in the `Device Manager` and the dropdown menu in the
  top bar of the IDE

Should you run into problems, maybe have a
look [here](https://developer.android.com/studio/run/emulator).
<br><br>

#### Run or debug your application

To run your application, it has to be installed to the desired target device. To start this process,
follow these steps:

- Look that the correct device is selected in the dropdown menu at the top bar of the IDE
- To run the application, click the `Run` button in the top bar or click here: `app`
- To debug the app, click the `Debug` button in the top bar. See the hints on debugging below.
- If you made only small changes since the last install, you can click the `Apply changes` button in
  the top bar. This only applies your changes to the running app instead of stopping, reinstalling
  and restarting it, and by this saves quite some time.

#### Hints on debugging

If you want to debug your app, you can use the usual way you learned to debug Java programs, so you
set breakpoints in the code and start the debugger. This can give you valuable insights in the
application's state and help you in finding bugs faster. Note that debugging can be imprecise or
lead to strange results when debugging a graphical user interface as we commonly have in mobile
apps,
as the updating of the screen happens somewhat asynchronous.  
When wishing to print text for debugging and logging purposes, I would prefer the `Log` library
over `System.out.println`. Here is an example how to use it:

```java
import android.util.Log;

public class MainActivity extends AppCompatActivity {
    String TAG = "MainActivity";
    int x = 5;
    //...

    public void move() {
        x--;
        Log.d(TAG, "x value is " + x);
        if (x < 0) {
            Log.w(TAG, "x smaller than 0!");
        }
    }
}
```

There are different methods for different log levels, this means messages of different importance.
From very unimportant to very important, these are:

- `Log.v(...)`: verbose, tells everything
- `Log.d(...)`: debug, used to give debugging information
- `Log.i(...)`: info, used to inform about certain events
- `Log.w(...)`: warn, used for situations that are not desired and could cause problems
- `Log.e(...)`: error, used to log errors
- `Log.wtf(...)`: what a terrible failure (no joke!), used for situations that should never occur
  Any of these takes two Strings, the first to tell where the log comes from, the second for the
  message

### 6. Enhance and improve the app

Congratulations if you have come so far. Now, the fun begins! Try to implement own features, change
default values, replace images, extend the game with whatever you like and play around!
