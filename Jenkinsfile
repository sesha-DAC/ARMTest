node {
    withEnv(["PATH+ANSIBLE=${tool 'ansible-2.4.2.0'}"]) {

        stage 'Init Working Env'
        sh 'sudo /opt/vars/init.sh'

        stage 'Check List'
        sh 'ls -alrt'

        stage 'Check Ansible Availability'
        sh 'which ansible'

        stage 'Check Ansible Version'
        sh 'ansible --version'

//        stage 'Git Update'
//        git url: repositoryUrl, credentialsId: "DAC-2018-1110", branch: branch
        
        stage 'Package Pre-Check'
        sh("ls -ltrhR")
        
        stage 'Run Playbook Tasks'
        ansiblePlaybook (
            playbook: "./ARMTest/src/armtemplate.yml",
            sudo: true
        )

        stage "Tasks Logged"
        sh 'sudo /opt/vars/log.sh "VMs powered on"'
    }
}

