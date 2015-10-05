# GAE issue: queue.yaml vs module

### Summary
This project demoes a bug that prevent queue.yaml file to be loaded/interpreted in the development server when modules are started. This is issue does not affect deployed apps.

### Environment
  - GoogleAppEngineLauncher 1.9.23.290
  - MacOS 10.10.5
  - PHP app with two modules (the default and another one) and a queue.yaml file

### Steps to reproduce
Launch the demo project without any launch settings so nly the default module will be launched.
If you go to the local dashboard in the Task Queues tab (http://localhost:8000/taskqueue), you will see that all the custom queues defined in queue.yaml will be there.

Launch the demo project with the full path of the 'analytics' module as an extra flag of the launch settings so the default module and the analytics one will be launched.
Now if you go to the local dashboard/Task Queues tab, you will see that there will only be the default queue!

Of course, trying to push tasks to the defined custom queues while modules are launched raise exceptions. I mean, it's not just an issue of the local dashboard that doesn't show queues, the queues aren't created at all.
