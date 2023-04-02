(dt-other-accounts)=
# Third-party accounts

(dt-account-github)=
## GitHub 

Duckietown uses [GitHub](https://github.com/duckietown) to distribute its open-source code and engage with
collaborators and end-users.
You will find it useful to have an account on GitHub. If you do not have one already, 
you can sign up for one at [this link](https://github.com/join).


(dt-account-dockerhub)=
## DockerHub

Duckietown uses [DockerHub](https://hub.docker.com/duckietown) to distribute the containerized version 
of its software modules.
If you are a developer, you will find it useful to have a DOckerHub account. If you do not have one already,
you can sign up for one at [this link](https://hub.docker.com/signup).


(dt-account-dockerhub-shell-credentials)=
### Configure the Duckietown Shell

The [Duckietown Challenges Server](https://challenges.duckietown.org) allows you to participate in robotics
competitions, submit class homeworks, etc., by uploading your work, packaged as a Docker image, to DockerHub.

Use the following command to give your DockerHub credentials to the Duckietown Shell so that your work
can be seamlessly uploaded to DockerHub on your behalf and for the Duckietown Challenges Server to 
evaluate your work on the cloud.

    dts challenges config --docker-username USERNAME --docker-password PASSWORD

where, `USERNAME` and `PASSWORD` need to be replaced with your DockerHub credentials.
