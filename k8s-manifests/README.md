#Para adicionar o repositório no argocd via CLI
argocd repo add git@github.com:[seu-usuario]/fortune-cookie.git \
  --ssh-private-key-path ~/.ssh/argocd.rsa

#Para criar a aplicação no argocd via CLI
argocd app create fortune-cookie \
--repo git@github.com:[seu-usuario]/fortune-cookie.git \
--path k8s-manifests \
--dest-server https://kubernetes.default.svc \
--dest-namespace default \
--revision argocd

#Legenda
--repo: URL do repositório Git contendo os manifestos.
--path: Caminho dentro do repositório onde os manifestos estão localizados.
--dest-server: URL do servidor Kubernetes onde a aplicação será implantada.
--dest-namespace: Namespace do Kubernetes onde os recursos serão criados.
--revision: Branch ou revisão do repositório a ser utilizada.
