# gitops-conclusion-code-cafe

## Handson ArgoCD
### Prereqs
- Github toegang tot https://github.com/BDelleman/gitops-conclusion-code-cafe --> Geef je GitHub username door aan Bart
- Toegang tot OpenShift --> check even de lijst met users in de [clusterconfig folder](./clusterconfig/values.yaml), password staat in de presentatie. Indien je er nog niet in staat geef dit even aan.

### Opzetten source folder
- Kopieer de inhoud van de demo folder en plaats deze in een nieuwe folder onder handson/apps. Vernoem de nieuwe folder naar jezelf
- Pas alleen de namespace in de gekopieerde values.yaml aan, zodat deze naar je eigen namespace verwijst. Namespace naam is je eigen voor- en achternaam in lowercase --> Dennis van den Boom wordt dennisvandenboom
- Commit en push de wijzigingen naar de repo
### Configureren ArgoCD
- Log in op OpenShift (https://console-openshift-console.apps.g9e68gsw.westeurope.aroapp.io/) 
	- Inlognaam Openshift: volledige naam aan elkaar, met hoofdletter voor en achternaam --> Dennis van den Boom wordt DennisvandenBoom
    - Password staat in presentatie
- In de menubalk bovenin klik op de 9 witte vierkantjes en vervolgens op 'Cluster Argo CD'
- Klik op 'Log in via OpenShift' -> htpasswd-provider -> jouw username en password
- Maak een nieuwe Application aan via '+ New App'
- Invulvelden, de rest leeg of default laten: 
	- Application name: verzin een unieke, herkenbare naam
	- Project name: default
	- Repository URL: kies uit de dropdown de github repo
	- Path: path naar jouw folder in de repo -> handson/apps/..
	- Cluster URL: https://kubernetes.default.svc
	- Dropdown waar default 'Directory' staat: kies Helm
	- Values files: values.yaml
- Bij juist aanmaken zie je nu dat de inhoud van jouw folder in de argocd application zichtbaar wordt
- Klik op 'Sync' om alles in OpenShift aan te laten maken
### Downloaden van tools
- Download oc commandline tool: menubalk in OpenShift --> vraagteken --> Command line tools
- Download VNC Viewer om de game daadwerkelijk te kunnen spelen: https://sourceforge.net/projects/tigervnc/files/stable/
### Opzetten connectie
- Ga naar de OpenShift console in een browser, klik op je username rechtsboven en vervolgens op 'Copy login command'. 
- Voer uit in een terminal: `oc login --token=<jouw-token> --server=https://api.g9e68gsw.westeurope.aroapp.io:6443`
- Start portforwarding vanuit het cluster naar localhost dmv het uitvoeren van het volgende commando in dezelfde terminal: `oc port-forward deployment/ocpdoom -n <jouw namespace naam> 5900:5900`
- Start vnc viewer en maak connectie op localhost:5900
	- password: openshift

### Gamen maar!
- pijltjes toetsen = lopen
- CTRL = schieten
- spatie = deuren openen