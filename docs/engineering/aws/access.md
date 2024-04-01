```markdown
### AWSCLI Installation

We execute the installation:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

## Configuration:

### Format of Configuration and Credentials Files

The `config` and `credentials` files are organized into sections. Sections include profiles, `sso-sessions`, and services. A section is a named collection of configurations and continues until another section definition line is found. Multiple profiles and sections can be stored in the `config` and `credentials` files.

They are plain text files that use the following format:

- Section names appear in brackets `[ ]` such as `[default]`, `[profile user1]`, and `[sso-session]`.
- All entries in a section adopt the general format of `setting_name=value`.
- Lines can be commented out if they start with a hash character `(#)`.

The `config` and `credentials` files contain the following types of sections:

We configure the `config` and `credentials` files in the `./aws` folder
- In `Credentials`

```ini
[default]
aws_access_key_id = 
aws_secret_access_key =

[tr-dev]
role_arn = 
source_profile = 

[tr-prod]
role_arn = 
source_profile = 

[trocglobal]
region = 
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
mfa_serial=
```

## Before installing AWSUME, we install:

### Installing pyenv:

We install the pyenv program.

```bash
curl https://pyenv.run | bash
```

Execute the following command to export the configuration to `.bashrc`:

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init --path)"' >> ~/.bashrc
```

Once pyenv is installed, we proceed to verify if it is working correctly with the following commands:

```bash
pyenv install --list  # Verify available versions
pyenv install 3.10.12  # Select a version to install
```

Within the navigator directory, activate the virtual environment env:

Create the Python virtual environment:

```bash
pyenv local 3.10.12
python -V
```

Then, activate the virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
```

### AWSUME Installation

```bash
pip install awsume
```

### Alias

The alias is necessary for Unix-type systems and shells, including Bash and Zsh. It is not necessary for Windows-type shells like PowerShell or Windows Command Prompt.

The alias should be defined in your shell's startup file, so it loads in every shell session. It should look something like this:

We adjust the awsume alias to be detected from pyenv.

```bash
alias awsume=". $(pyenv which awsume)"
```


AWSUME will take the configuration from `.aws/` and the credentials, and we will be able to execute aws commands.

For connecting to dev --> `awsume tr-dev`
- We will be prompted for our MFA code and logged into Amazon.

For production --> `awsume tr-prod`

Note: to switch environments, an update of the aws regions is required, for that we can apply the following command:
```bash
aws eks --region us-east-2 update-kubeconfig --name trocglobal-services
```

This Markdown manual provides a step-by-step guide for installing AWSCLI and AWSUME, including configuring `pyenv` and managing Python virtual environments.
```