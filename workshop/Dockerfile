# Ubuntu base image
FROM ubuntu:16.04


# Install any needed packages specified in requirements.txt
RUN apt update
RUN apt install -y man
RUN apt install bwa
RUN apt install samtools
#RUN apt install bedtools
RUN apt install -y wget && apt install -y unzip && apt install -y perl
RUN apt-get update && apt install -y make && apt install -y g++ && apt install -y libz-dev && apt install -y python && wget --no-check-certificate https://github.com/arq5x/bedtools2/releases/download/v2.26.0/bedtools-2.26.0.tar.gz && tar -zxvf bedtools-2.26.0.tar.gz && cd bedtools2 && make
#RUN apt install -y picard

#Install Java
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:openjdk-r/ppa 
RUN apt-get update 
RUN apt-get install --fix-missing -y -f openjdk-7-jre

#Install FastQC

RUN wget --no-check-certificate https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.11.5.zip && unzip fastqc_v0.11.5.zip && chmod ug+x /FastQC/fastqc




# Define commonly used JAVA_HOME variable
ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-amd64

# Define environment variable
ENV NAME World

#ENV PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/FastQC

#Add fastq-dump
RUN wget --no-check-certificate https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/current/sratoolkit.current-ubuntu64.tar.gz && tar -xvf sratoolkit.current-ubuntu64.tar.gz

# Copy ref genome info into the container at /data
ADD data/refs/pathogen_ref.* /data/refs/
#ADD data/fastqs/*.fastq.gz /data/fastqs/
ADD scripts/* /scripts/

ENV PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/FastQC:/sratoolkit.2.8.2-1-ubuntu64/bin:/bedtools2/bin

# Define working directory.
WORKDIR /data

#Bash shell
CMD /bin/bash
