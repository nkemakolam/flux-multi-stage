# flux-multi-stage
Here are the steps i used to test the compactibility and switchin of Helm and flux operator on a locall minikube.
Steps :

1. first start a  new profile cluster on your local minikube
`minikube start --profile mini-acpt`
this would creat for you a clean cluster instance to worl with.
2. Create a git repo on your gihub account and then clone that repo locally
`https://github.com/nkemakolam/flux-multi-stage.git`
3. Switch to the the context that you using the kubectx command if you have it installed `kubectx mini-acpt`
5. Then create a namaespace called flux or anything you like.
`kubectl create ns flux`
6. Export your GHUSER which is the name os your github account
`export GHUSER="your username"
7. run this flux installation helm command
 fluxctl install \
--git-user=${GHUSER} \
--git-email=${GHUSER}@users.noreply.github.com \
--git-path=acpt \
--manifest-generation=true \
--git-url=git@github.com:${GHUSER}/flux-multi-stage \
--namespace=flux | kubectl apply -f - 

8. once this command succefully run the to generate the public key of flux run the followimh command
`fluxctl identity --k8s-fwd-ns flux`

