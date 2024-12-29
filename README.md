
DISCLAIMER - ABANDONED/UNMAINTAINED CODE / DO NOT USE
=======================================================
While this repository has been inactive for some time, this formal notice, issued on **December 10, 2024**, serves as the official declaration to clarify the situation. Consequently, this repository and all associated resources (including related projects, code, documentation, and distributed packages such as Docker images, PyPI packages, etc.) are now explicitly declared **unmaintained** and **abandoned**.

I would like to remind everyone that this project’s free license has always been based on the principle that the software is provided "AS-IS", without any warranty or expectation of liability or maintenance from the maintainer.
As such, it is used solely at the user's own risk, with no warranty or liability from the maintainer, including but not limited to any damages arising from its use.

Due to the enactment of the Cyber Resilience Act (EU Regulation 2024/2847), which significantly alters the regulatory framework, including penalties of up to €15M, combined with its demands for **unpaid** and **indefinite** liability, it has become untenable for me to continue maintaining all my Open Source Projects as a natural person.
The new regulations impose personal liability risks and create an unacceptable burden, regardless of my personal situation now or in the future, particularly when the work is done voluntarily and without compensation.

**No further technical support, updates (including security patches), or maintenance, of any kind, will be provided.**

These resources may remain online, but solely for public archiving, documentation, and educational purposes.

Users are strongly advised not to use these resources in any active or production-related projects, and to seek alternative solutions that comply with the new legal requirements (EU CRA).

**Using these resources outside of these contexts is strictly prohibited and is done at your own risk.**

Regarding the potential transfer of the project to another entity, discussions are ongoing, but no final decision has been made yet. As a last resort, if the project and its associated resources are not transferred, I may begin removing any published resources related to this project (e.g., from PyPI, Docker Hub, GitHub, etc.) starting **March 15, 2025**, especially if the CRA’s risks remain disproportionate.

# Docker SDK for Python

[![Build Status](https://travis-ci.org/docker/docker-py.svg?branch=master)](https://travis-ci.org/docker/docker-py)

A Python library for the Docker Engine API. It lets you do anything the `docker` command does, but from within Python apps – run containers, manage containers, manage Swarms, etc.

## Installation

The latest stable version [is available on PyPI](https://pypi.python.org/pypi/docker/). Either add `docker` to your `requirements.txt` file or install with pip:

    pip install docker

If you are intending to connect to a docker host via TLS, add `docker[tls]` to your requirements instead, or install with pip:

    pip install docker[tls]

## Usage

Connect to Docker using the default socket or the configuration in your environment:

```python
import docker
client = docker.from_env()
```

You can run containers:

```python
>>> client.containers.run("ubuntu:latest", "echo hello world")
'hello world\n'
```

You can run containers in the background:

```python
>>> client.containers.run("bfirsh/reticulate-splines", detach=True)
<Container '45e6d2de7c54'>
```

You can manage containers:

```python
>>> client.containers.list()
[<Container '45e6d2de7c54'>, <Container 'db18e4f20eaa'>, ...]

>>> container = client.containers.get('45e6d2de7c54')

>>> container.attrs['Config']['Image']
"bfirsh/reticulate-splines"

>>> container.logs()
"Reticulating spline 1...\n"

>>> container.stop()
```

You can stream logs:

```python
>>> for line in container.logs(stream=True):
...   print line.strip()
Reticulating spline 2...
Reticulating spline 3...
...
```

You can manage images:

```python
>>> client.images.pull('nginx')
<Image 'nginx'>

>>> client.images.list()
[<Image 'ubuntu'>, <Image 'nginx'>, ...]
```

[Read the full documentation](https://docker-py.readthedocs.io) to see everything you can do.
