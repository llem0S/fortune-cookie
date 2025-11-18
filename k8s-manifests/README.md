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

#CI/CD
O CI/CD (Integração e Entrega Contínua) garante que mudanças no código sejam testadas e entregues de forma automática e confiável.

Integração Contínua (CI)
A Integração Contínua (CI) é a prática de integrar frequentemente as mudanças de código em um repositório compartilhado. Cada vez que um desenvolvedor faz uma alteração, essa mudança é automaticamente testada e integrada ao código principal. Isso ajuda a identificar rapidamente problemas e conflitos, garantindo que o código sempre esteja em um estado funcional. A CI pode ser configurada com ferramentas de automação como GitHub Actions, GitLab CI, Jenkins, entre outras. O fluxo típico de CI envolve:

O desenvolvedor faz uma alteração no código e envia para o repositório (push).
A ferramenta de CI detecta a alteração e executa uma série de testes automatizados.
Se os testes forem aprovados, a alteração é integrada ao código principal.
Entrega Contínua (CD)
A Entrega Contínua (CD) é a prática de automatizar a entrega de software para ambientes de produção ou pré-produção. Enquanto a Integração Contínua (CI) foca em testes e integração, a CD garante que cada mudança no código seja automaticamente preparada para ser implantada em produção, se necessário. Isso inclui etapas como:

Construção da imagem do container;
Execução de testes de integração;
Validação do estado da aplicação.
No fluxo de CD, após a integração do código, as seguintes etapas podem ser realizadas:

Build: Gerar a imagem do container ou o artefato do aplicativo.
Testes: Executar testes adicionais (testes de integração, testes de carga, etc.).
Deploy: Implantar automaticamente a versão mais recente da aplicação em um ambiente de produção ou homologação, dependendo da configuração. Essa sequência automatizada de etapas é chamada de pipeline.
Pipeline de CI/CD
No contexto de CI/CD, uma pipeline é usada para integrar código (CI) e entregar a versão final para produção (CD), de forma automatizada. Para aplicar essas práticas corretamente, é essencial entender:

Como versionar código (Git);
Como empacotar e orquestrar containers (Docker e Kubernetes).
Cada etapa da pipeline é uma tarefa, como compilar o código, rodar testes ou fazer o deploy da aplicação. Essas tarefas são executadas de forma contínua sempre que há uma mudança no código, garantindo um fluxo eficiente e sem interrupções.
