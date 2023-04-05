# .NET Helm Chart
Um chart Helm para implantar uma aplicação [.NET](https://dot.net/) no OpenShift.

## Values
Abaixo está uma tabela de cada um dos valores usados para configurar esse chart.

| Valor | Descrição | Default | Informação adicional |
| ----- | ----------- | ------- | ---------------------- |
| `image.name` | Nome da imagem que deseja implantar (não colocar caminho do nexus) | | O chart vai configurar para imagem ser obtida do nexus baseado nesse valor. |
| `image.tag` | Tag que deseja implantar |  | O chart vai configurar a tag da imagem baseado nesse valor |
| `deploy.replicas` | Número de replicas para implantar |  | - |
| `deploy.resources` | Formulário livre para `resources` | - | Mais informações: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| `deploy.serviceType` | Tipo de serviço para criar | `ClusterIP` | Mais informações: https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types |
| `deploy.ports` | Formulário livre para service `ports`. | Veja [values.yaml](./values.yaml) | Mais informações: https://kubernetes.io/docs/concepts/services-networking/service/#defining-a-service |
| `deploy.route.enabled` | Define se uma Rota deve ser criada | `true` | Permite clientes fora do Openshift acessar sua aplicação|
| `deploy.route.targetPort` | A porta que a Rota vai direcionar o tráfego | `http` | - |
| `deploy.route.tls.enabled` | Define se a Rota deve ter TLS | `true` | Mais informações: https://docs.openshift.com/container-platform/4.6/networking/routes/secured-routes.html |
| `deploy.route.tls.termination` | Determina o tipo de TLS para usar | `edge` | Opções: `edge`, `reencrypt`, `passthrough` |
| `deploy.route.tls.insecureEdgeTerminationPolicy` | Define se o trafego inseguro deve ser redireiconado | `Redirect` | Opções: "Allow", "Disable", "Redirect" |
| `deploy.route.tls.key` | Fornece conteúdo do arquivo key | - | Isso é confidencial. Não coloque esse valor no git. |
| `deploy.route.tls.caCertificate` | Fornece o conteúdo do certificado da autoridade certificadora | - | - |
| `deploy.route.tls.certificate` | Fornece o conteúdo do certificado| - | - |
| `deploy.route.tls.destinationCACertificate` | Fornece o certificado CA de destino | - | - |
| `deploy.livenessProbe` | Formulário livre para `livenessProbe`. | Veja [values.yaml](./values.yaml) | Mais informações: https://docs.openshift.com/container-platform/4.6/applications/application-health.html#application-health-about_application-health |
| `deploy.readinessProbe` | Formulário livre para `readinessProbe`. | Veja [values.yaml](./values.yaml) | Mais informações: https://docs.openshift.com/container-platform/4.6/applications/application-health.html#application-health-about_application-health |
| `deploy.env` | Formulário livre para `env` | - | Mais informações: https://kubernetes.io/docs/tasks/inject-data-application/define-environment-variable-container/ |
| `deploy.envFrom` | Formulário livre para `envFrom` | - | Mais informações: https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/#configure-all-key-value-pairs-in-a-configmap-as-container-environment-variables |
| `deploy.applicationProperties.enabled` | Define se a propriedade da aplicação deve ser externalizada | `false` | - |
| `deploy.applicationProperties.mountPath` | Local para montar o arquivo de propriedades| `/deployments/config/` | - |
| `deploy.applicationProperties.properties` | O conteúdo das propriedades da aplicação| - | - |
| `deploy.volumeMounts` | Formulário livre para volume mounts | - | Mais informações: https://kubernetes.io/docs/concepts/storage/volumes/ |
| `deploy.volumes` | Formulário livre para volumes | - | Mais informações: https://kubernetes.io/docs/concepts/storage/volumes/ |
| `deploy.initContainers` | Formulário livre para init containers | - | Mais informações: https://kubernetes.io/docs/concepts/workloads/pods/init-containers/ |
| `deploy.extraContainers` | Formulário livre para containers | - | Mais informações: https://kubernetes.io/docs/concepts/workloads/pods/#pod-templates |
| `global.nameOverride` | Sobrescreve o nome da release| - | Recursos são nomeados com nome da release. Configure esse valor para sobrescrever o nome da release. |
