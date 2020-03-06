#! sensationnel

def deployBranches = [ " master " ]
phase def =  " vérifier "

étape ( ' Build ' ) {
    nœud {
        caisse scm
        branche def = scm . branches [ 0 ] . Nom
        if (deployBranches . contient (branche)) {
            phase =  " déployer "
        }
        echo " Exécuter mvn $ p hase sur la branche $ b ranch "
        sh ' mkdir -p ~ / .gnupg '
        withCredentials ([
            fichier ( credentialsId : ' gpg-pubring ' , variable : ' GPG_PUB_RING ' ),
            fichier ( credentialsId : ' gpg-secring ' , variable : ' GPG_SEC_RING ' ),
            fichier ( credentialsId : ' gradle-settings ' , variable : ' GRADLE_SETTINGS ' )]) {
                essayez {
                    sh " ./gradlew $ p hase -P signature.secretKeyRingFile = $ G PG_SEC_RING -P extProps = $ G RADLE_SETTINGS "
                } enfin {
                    archiveArtifacts ' build / libs / *. jar '
                    archiveArtifacts ' build / libs / *. asc '
                    if (phase ==  ' deploy ' ) archiveArtifacts ' build / poms / *. xml '
                    if (phase ==  ' deploy ' ) archiveArtifacts ' build / poms / *. asc '
                    junit allowEmptyResults : true , testResults : ' build / test-results / test / *. xml '
                }
        }
        étape ([$ class : ' WsCleanup ' ])
    }
}
