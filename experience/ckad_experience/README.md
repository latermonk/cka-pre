Resources
KUBERNETES CLUSTER
local https://github.com/kubernetes-sigs/kind (or just use minikube if it works for you)
cloud https://cloud.google.com/kubernetes-engine (for PersistentVolume and Ingress, I needed to try the real deal)
practice environment: https://github.com/arush-sal/cka-practice-environment
PRACTICE
exercises: https://github.com/dgkanatsios/CKAD-exercises (this is basically the kind of questions you're going to have during the exam)
bookmarks for docs made by @rocketman: https://drive.google.com/open?id=1HWXRNyHawuE29VkAzu5Df9Z8txAs8Wbn
ARTICLE
https://medium.com/chotot-techblog/tips-tricks-to-pass-certified-kubernetes-application-developer-ckad-exam-67c9e1b32e6e
https://linuxacademy.com/community/posts/show/topic/25094-cka-exam-experience-and-some-useful-tips
VIDEO
NodePort, LoadBalancer, Ingress: https://www.youtube.com/watch?v=HwogE64wjmw
Storage (PV/PVC): https://www.youtube.com/watch?v=n06kKYS6LZE
HONORABLE MENTION
All the resources are in the Kubernauts list https://docs.google.com/spreadsheets/d/10NltoF_6y3mBwUzQ4bcQLQfCE1BWSgUDcJXy-Qp2JEU/edit#gid=0
Tips
questions have a weight, I didn't even read questions with less than 5% on my first pass, I just wrote the number down in the note thingy and did them after all the more valuable questions were done.
Use the note thingy because you have no way of knowing if you completed a question or not, unless you read the question again and check the cluster which is time consuming.
make sure you are working on the right cluster by setting the context at the beginning of each questions. The command is given to you, it will avoid to work on the wrong cluster! (ask me how I know that.....(-_-') )
remember to click on the button "end the exam"! I was there for 2 minutes not touching the keyboard wondering why this thing isn't over yet until the proctor reminded me. The button is hidden into the exam settings menu or something like that. A visible button would be nice though because after a 2h high-focus exam, no way I remember that kind of details.
before the exam starts, you have to remove all drinks and food, show your ID and show your desktop. I use a laptop with an external monitor so pro-tip: Make sure your cables are long enough or disconnect them completely. (again ask me how I know that.....(-_-') )
You can't read out loud or cover your mouth. I had no idea how hard that was until I actually tried!! No kidding.
just relax if you see something like "configure fluentd" or "HAproxy". No configuration of external tools will be asked of you! The config file is usually provided.
only the kubernetes.io/docs is allowed, know the examples of the documentation (see bookmarks for docs made by @rocketman). It saved me a lot of time to copy/paste examples and adapt them. Make sure the object names/labels are correct. (ok don't ask me how I know that one....)
knowing the basics of vim will help: https://devhints.io/vim
a few times I had to use cat pod.yaml | sudo tee -a /opt/some/long/cryptic/file.yaml because the file access was root and it was already created. I didn't know if I could overwrite the file with a sudo cp or not.
learn to use kubectl explain pod.spec.XXX, it saves time. Although a simple search in the k8s.io/docs might give you the answer too.
the problem with the k8s.io/docs is that a CTRL-F/CMD-F might yield results hidden in the left side menu which confused the hell out of me first.
Using the latest version (1.13) of the documentation was totally fine by me. No need to go back to 1.11 or 1.12
check out the help with kubectl bla bla -h, there is usually good examples that you can just copy/paste/adapt.
use autocomplete and learn how to use efficiently.
alias k=kubectl
source <(kubectl completion bash) # completion will save a lot of time and avoid typo
source <(kubectl completion bash | sed 's/kubectl/k/g' ) # so completion works with the alias "k"

## good to know
k get po -n prod[TAB]uction # will autocomplete the namespace
k describe po -n production [TAB] # will list the pods in the namespace "production"
I hope it helps.