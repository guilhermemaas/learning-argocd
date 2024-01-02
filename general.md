Aplication source type:
- Arquivos .yaml (Manifestos k8s), como deployments, services, namespaces, configmaps, volumes, etc.
- Repositórios Helm

Target state:
- O meu objetivo, ou seja, é o que está no repositório git.
- Vai rodar o "Sync" para chegar nesse estado desejado. Alterações manuais podem ser sobrepostas

Live state:
- Estado atual de um app que está sendo executado no cluster k8s.
- Por exemplo, no meu manifesto do deployment, eu tenho 5 réplicas, alguém manualmente com edit alterou pelo kubectl para 10.
Teríamos uma diferença entre o "Live state" e o "Target state".

Sync status:
- É o estado do sync entre o repositório git (Target state) e o cluster Kubernetes (Live state).
- Tipos de Status:
    - Synced: Sincronizado.
    - OutOfSync: Fora de sincronia.
    - Unknown: Desconhecido.
        - O ArgoCD não conseguiu verificar o estado da sincronia.
        - Problema de comunicação entre o Argo e o Git/Cluster.
    
Sync operation status:
- Resultado de uma operação de sync em uma aplicação no cluster k8s.
- Tipos de Sync operation status:
    - Sucessful
        - Operação de Sync concluída com sucesso.
    - Failed
        - Operação de Sync falhou.
    - In Process
        - Operação em andamento.

    - Unknown:
        - Argo não conseguiu determinar o estado atual da operação de sincronização.

Refresh:
- Força o ArgoCD a buscar as últimas informações no repositório Git.
- O Refresh apenas atualiza o estado do "app" no ArgoCD, para aplicar as alterações deve-se clicar em "Sync".


Health:
- A saúde dos recursos de uma App que está sendo implantanda no cluster Kubernetes.
- Existem alguns tipos de estado health, como:
    - Healthy: Indica que um recurso está saudável e funcionando corretamente.
    - Degraded: Indica que um recurso está funcionando, mas pode estar com algum problema que pode afetar seu funcionamento.
    - Progressing: Indica que o recurso está em processo de implantação ou atualização.
    - Suspended: Indica que o recurso foi suspenso e não está sendo processado pelo ArgoCD.

    - Missing: Indica que o recurso está ausente ou não pode ser encontrado no cluster Kubernetes.

Boas práticas:
- Separating Config x Source Code Repositories.

Benefícios:
- Implantações automatizadas.
- Sincronização contínua (Monitorar a alteração os arquivos no git) e implementar a atualização automática.
- Declaratividade e versionamento.
- GitOps.
- Uma instalação pode operar em diferentes clusters.