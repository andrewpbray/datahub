# Should match the hub image used by version of chart in hub/requirements.yaml
# If that changes, this should be changed too!
FROM jupyterhub/k8s-hub:1.1.2

USER root

# npm is needed to install JupyterHub from source
RUN apt update > /dev/null  && apt install --yes npm > /dev/null

# Brings in https://github.com/jupyterhub/jupyterhub/pull/3579
# and https://github.com/jupyterhub/jupyterhub/pull/3639
RUN python3 -m pip install --no-cache --force-reinstall --upgrade git+https://github.com/jupyterhub/jupyterhub.git@69a1e97fbee1711e3fdb5fd795e349a4eb395060

COPY canvasauthenticator /srv/canvasauthenticator
RUN python3 -m pip install --no-cache /srv/canvasauthenticator

USER ${NB_USER}
