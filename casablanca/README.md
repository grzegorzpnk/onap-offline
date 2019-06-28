This is a guide how to install ONAP using ONAP Operations Manager (OOM).

When you have up and running ONAP UnderCloud (see heat/ directory) you can proceed to ONAP installation.

Login to Rancher VM. You should have *kubectl* configured. Check it by using:

`kubectl get pods --all-namespaces`

Firstly you need to download this repository.

`git clone http://10.254.188.33/onap/integration-advnet.git`

`cd beijing/`

Download OOM repository.

`git clone -b beijing http://gerrit.onap.org/r/oom`

Override ONAP configuration.

Modify config/onap/values.yaml and config/robot/values.yaml. Adjust configuration parameters to you environment. In order to generate encrypted password use enc_passwd.sh script located in *utils/* directory.

`cp config/onap/values.yaml oom/kubernetes/onap/values.yaml`

`cp config/robot/values.yaml oom/kubernetes/robot/values.yaml`

Make sure that oom/kubernetes/robot/demo-k8s.sh and oom/kubernetes/robot/ete-k8s.sh are runnable.

`chmod +x oom/kubernetes/robot/demo-k8s.sh`

`chmod +x om/kubernetes/robot/ete-k8s.sh`

When the configuration is ready you can run ONAP installation.

`sudo ./cd.sh -b beijing -e onap -c false`

**Note!** Do not change script's arguments.

The installation process will start. It takes about 1h to complete. Then, you should have all ONAP services up and running.

The next step is to configure ONAP instance. Enter Robot directory and execute commands in the following order:

`cd oom/kubernetes/robot/`

`./demo-k8s.sh onap distribute`

`./demo-k8s.sh onap init`

### More information ###

Additional tips and instructions you can find on official ONAP sites:

https://onap.readthedocs.io/en/beijing/submodules/oom.git/docs/index.html

https://onap.readthedocs.io/en/beijing/submodules/oom.git/docs/oom_quickstart_guide.html

https://onap.readthedocs.io/en/beijing/submodules/oom.git/docs/oom_user_guide.html

