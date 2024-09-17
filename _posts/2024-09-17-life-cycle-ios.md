# State Changes in an iOS app
An iOS application can transition between the following states:
1. Not running
2. InActive
3. Active
4. Background
5. Suspend


![State Changes in an iOS App](https://i.imgur.com/aeOPsHh.png)
### State: Not Running
The app is not running. It may be in this state if it has not yet been launched or has been terminated by the system or the user.
### State: In Active
The app is running but not receive any events. The state between active state and background state, such as when a call phone or text received
### State: Active
The app is running in the foreground and receiving events. This is the state where the app is fully interactive and responsive to user inputs.
### State: Background
The app is running in the background but not visible to the user. The app can execute code in the background for a short period (e.g., for saving data or completing tasks) before it is suspended. Background tasks include handling location updates, playing audio, etc.
### State: Suspended
The app is in the background and not executing any code. The system may terminate suspended apps to reclaim resources if needed. The app remains in memory but is not actively running.

# Lifecycle Methods in ```ApplicationDelegate```
- ```application(_:didFinishLaunchingWithOptions:)```: Called when the app has completed launching and is about to run. This is where you typically perform app setup.
* applicationDidBecomeActive(_:): Called when the app transitions from inactive to active state. You should use this to restart any tasks that were paused or not yet started when the app was inactive.
* applicationWillResignActive(_:): Called when the app is about to move from active to inactive state. Use this to pause ongoing tasks or disable features that shouldn’t run while the app is inactive.
* applicationDidEnterBackground(_:): Called when the app moves to the background. This is where you should save user data, release shared resources, and store enough state information to restore the app to its current state if it is terminated later.
* applicationWillEnterForeground(_:): Called as part of the transition from the background to the active state. This is where you can undo changes made when entering the background.
* applicationWillTerminate(_:): Called when the app is about to terminate. This method is not called if the app is suspended or if it is being terminated by the system. It is primarily used for final cleanup.
