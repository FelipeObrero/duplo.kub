# duplo.kub


- creare progetto
```
npx create-react-app duplo.kub
```

- aggiungere file:

    - **Dockerfile**<br>
    Il Dockerfile conterrà i comandi che la pipeline CI/CD Jenkins utilizzerà per creare l'<u>immagine</u> Docker per la semplice applicazione React.js.

    - **deployment.yaml**<br>
    Il file YAML di distribuzione Kubernetes crea i <u>pod</u> per il contenitore dell'applicazione React.js nel cluster Kubernetes. I pod ospiteranno il contenitore dell'applicazione e ogni pod avrà le risorse Kubernetes necessarie: creerà due pod nell'applicazione Kubernertes; estrarrà l'immagine Docker dal repository Docker Hub e creerà un'applicazione containerizzata. 

    - **service.yaml**<br>
    In file YAML di distribuzione del servizio Kubernetes creerà un <u>servizio</u> Kubernetes nel cluster Kubernetes. Il servizio Kubernetes esporrà i pod per il contenitore dell'applicazione React.js all'esterno del cluster Kubernetes. Utilizzerai il servizio Kubernetes per accedere al contenitore dell'applicazione React.js dall'esterno del cluster Kubernetes.

    - **Jenkinsfile**<br>
    Il "Jenkinsfile" avrà più fasi per definire la nostra <u>pipeline</u> Jenkins CI/CD.


> Il Jenkinsfile creerà una pipeline Jenkins con quattro fasi:
- Checkout Source:<br>
In questa fase, Jenkins utilizzerà il repository GitHub. Estrarrà ed eseguirà la scansione di tutti i file in questo repository GitHub.

- Build image:<br>
In questa fase della pipeline, utilizzerà il Dockerfile per creare una immagine Docker.

- Pushing Image:<br>
In questa fase invierà l'immagine Docker sul Docker Hub.

- Deploying container to Kubernetes:<br>
Infine estrarrà l'immagine dal repository Docker Hub e creerà un'applicazione containerizzata, che distribuirà sul contenitore su Kubernetes.

Biblio:
- https://sweetcode.io/how-to-deploy-an-application-to-kubernetes-cluster-using-jenkins-ci-cd-pipeline/
