# Alternative to AsyncTask in Java

The <b>AsyncTask</b> class helped us in executing some code in the background thread. With the help of AsyncTask we can execute something on the background thread and get the result back in the UI thread.

</b>But Android AsyncTask is deprecated in API Level 30.</b>

* <b>Why Android AsyncTask is Deprecated?</b>

    Here is the official reason it is deprecated.</br> 
    AsyncTask was intended to enable proper and easy use of the UI thread. However, the most common use case was for integrating into UI, and that would cause Context leaks, missed callbacks, or crashes on configuration changes. It also has inconsistent behavior on different versions of the platform, swallows exceptions from doInBackground, and does not provide much utility over using Executors directly.

* Alternative of AsyncTask
    The officially recommended alternative is [Kotlin Coroutines](https://developer.android.com/topic/libraries/architecture/coroutines), that you must use of writing Asynchronous Code in your project.

* Using Executors
    We have `java.util.concurrent.Executors` class; that we can use in place of AsyncTask if you do not wish to use <b>Kotlin Coroutines.</b>

    Here is an example how you can use it.

```
class DownloadTaskRunner {
            private Executor executor = Executors.newSingleThreadExecutor(); 
            private Handler handler = new Handler(Looper.getMainLooper());

            public void executeAsync() {
                executor.execute(new Runnable() {
                    @Override
                    public void run() {
                        /*
                        * Your task will be executed here
                        * you can execute anything here that
                        * you cannot execute in UI thread
                        * for example a network operation
                        * This is a background thread and you cannot
                        * access view elements here
                        *
                        * its like doInBackground()
                        * */

                        handler.post(new Runnable() {
                            @Override
                            public void run() {
                                /*
                                * You can perform any operation that
                                * requires UI Thread here.
                                *
                                * its like onPostExecute()
                                * */
                            }
                        });
                    }
                });
            }
        }
```
It is pretty much the same thing that you do using AsyncTask.


* Some useful resources
    1. [StackOverflow](https://stackoverflow.com/questions/58767733/android-asynctask-api-deprecating-in-android-11-what-are-the-alternatives/63500657#63500657)
    2. [Medium Blog](https://medium.com/code-yoga/some-great-alternatives-for-asynctasks-e8113747673a)
    3. [Simplified Coding](https://www.simplifiedcoding.net/android-asynctask/#:~:text=Alternative%20of%20AsyncTask,that%20I%20have%20already%20published.)