FROM ubuntu:22.04

# Source: https://code.visualstudio.com/remote/advancedcontainers/add-nonroot-user
RUN groupadd --gid 1000 juser \
    && useradd --uid 1000 --gid 1000 -m juser \
    && apt-get update \
    && apt-get install -y sudo \
    && echo juser ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/juser \
    && chmod 0440 /etc/sudoers.d/juser

USER juser

RUN sudo apt-get install -y \
    python3 \
    python3-venv 

WORKDIR /home/juser/notebook

RUN python3 -m venv /home/juser/venv
ENV PATH="/home/juser/venv/bin:$PATH"

RUN /home/juser/venv/bin/pip install notebook

# `--user`: installs the kernel for the current user.
# `--name`: is the internal name used by Jupyter to identify the kernel.
RUN /home/juser/venv/bin/python -m ipykernel install --user --name=jupyter-venv

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--NotebookApp.token=''", "--NotebookApp.password=''", "--ServerApp.disable_check_xsrf=True"]
