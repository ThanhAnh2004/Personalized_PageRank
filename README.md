# Triển khai Personalized PageRank với PySpark trên WSL Ubuntu
---

# Thiết lập môi trường (Ubuntu 22.04 trên WSL)

## Bước 1: Cài đặt WSL và các gói cơ bản

### Mở **PowerShell** hoặc **Terminal (Admin)** và chạy:

wsl --install

### Khởi động lại máy tính nếu được yêu cầu. Sau đó, mở WSL Ubuntu 22.04 và chạy các lệnh sau:

sudo apt update && sudo apt upgrade -y

sudo apt install python3 python3-pip -y

sudo apt install openjdk-11-jdk -y

## Bước 2: Tải và giải nén Apache Spark
### Tải Spark 3.4.4 đã được biên dịch với Hadoop 3:

wget https://archive.apache.org/dist/spark/spark-3.4.4/spark-3.4.4-bin-hadoop3.tgz

### Giải nén và đổi tên thư mục:

tar -xvzf spark-3.4.4-bin-hadoop3.tgz

mv spark-3.4.4-bin-hadoop3 sparkk

## Bước 3: Cấu hình biến môi trường
### Mở file ~/.bashrc để chỉnh sửa:

nano ~/.bashrc

export JAVA_HOME=/usr/lib/jvm/java-1.11.0-openjdk-amd64

export SPARK_HOME=/home/linux_user/sparkk

export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin

export PATH=$PATH:/home/linux_user/

### Lưu và thoát (Ctrl+O, Enter, Ctrl+X), sau đó tải lại cấu hình:

sudo apt install python3-venv python3-pip -y

python3 -m venv ~/pyspark_env

source ~/pyspark_env/bin/activate

## Bước 4: Cài đặt PySpark và thư viện hỗ trợ
### Cài đặt các gói cần thiết:

pip3 install pyspark==3.4.4

pip3 install cloudpickle==1.6.0

## Chạy chương trình
### Điều hướng đến thư mục chứa personalized_pagerank.py và chạy:

python3 personalized_pagerank.py

# LƯU Ý:
-Đảm bảo tất cả biến môi trường (JAVA_HOME, HADOOP_HOME, Path) được cập nhật sau mỗi bước.
-Nếu gặp lỗi, kiểm tra lại đường dẫn hoặc chạy CMD với quyền quản trị.
-Trước khi chạy nên khởi động chương trình trên môi trường máy ảo


