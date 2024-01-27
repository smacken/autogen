FROM mcr.microsoft.com/vscode/devcontainers/python:3.10

#
# Update the OS and maybe install packages
#
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
   && apt-get upgrade -y  \
   && apt-get -y install --no-install-recommends build-essential npm \
   && apt-get autoremove -y \
   && apt-get clean -y \
   && rm -rf /var/lib/apt/lists/*
ENV DEBIAN_FRONTEND=dialog

# For docs
RUN npm install --global yarn
RUN pip install pydoc-markdown

# Set environment variable if needed
# ENV OPENAI_API_KEY="{OpenAI-API-Key}"

# Install Python packages
RUN pip install --upgrade pip
RUN pip install pyautogen[teachable,lmm,retrievechat,mathchat,blendsearch] autogenra
RUN pip install numpy pandas matplotlib seaborn scikit-learn requests urllib3 nltk pillow pytest beautifulsoup4


# Expose port
EXPOSE 8081

# Start Command
CMD ["/bin/bash"]
