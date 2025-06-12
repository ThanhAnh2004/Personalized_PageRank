# Triển khai Personalized PageRank với PySpark trên WSL Ubuntu 

Kho lưu trữ này cung cấp hướng dẫn chi tiết để thiết lập môi trường Apache Spark trên Windows Subsystem for Linux (WSL) với Ubuntu 22.04 và triển khai thuật toán Personalized PageRank (PPR) theo yêu cầu của Bài toán 10.11. Việc triển khai dựa trên cấu trúc đồ thị được mô tả trong Hình 10.21 của bài toán.

### Thiết lập môi trường (Ubuntu 22.04 trên WSL)

## Bước 1. Cài đặt WSL và các gói cơ bản

# Mở PowerShell hoặc terminal (với quyền Admin) và chạy:

wsl --install

# Khởi động lại máy tính nếu được yêu cầu. Mở WSL Ubuntu 22.04 và cập nhật hệ thống, cài đặt các gói cần thiết:

sudo apt update && sudo apt upgrade -y
sudo apt install python3 python3-pip -y
sudo apt install openjdk-11-jdk -y

## Bước 2. Tải và giải nén Apache Spark
# Tải file nén Spark phiên bản 3.4.4 đã được biên dịch với Hadoop 3 từ trang lưu trữ chính thức của Apache:

wget https://archive.apache.org/dist/spark/spark3.4.4/spark-3.4.4-bin-hadoop3.tgz

# Giải nén file tar.gz:

tar -xvzf spark-3.4.4-bin-hadoop3.tgz

# Đổi tên thư mục cho dễ quản lý: 

mv spark-3.4.4-bin-hadoop3 sparkk

## Bước 33Cấu hình biến môi trường
# Mởfile cấu hình shell để chỉnh sửa biến môi trường:

 nano ~/.bashrc

# Thêm các dòng sau vào cuối file để cấu hình Java,Spark và đường dẫn:

 export JAVA_HOME=/usr/lib/jvm/java 1.11.0-openjdk-amd64
 export SPARK_HOME=/home/linux_user/sparkk
 export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin
 export PATH=$PATH:/home/linux_user/

# Lưu và thoát (nhấn Ctrl+O, Enter, Ctrl+X).
 # Tải lại file cấu hình:
 source ~/.bashrc

# Cài đặt môi trường máy ảo:

sudo apt install python3 venv python3-pip

# Tạo mới môi trường ảo:

python3 -m venv ~/pyspark_env

# Khởi động chương trình trên môi trường máy ảo

source ~/pyspark_env/bin/activate

## Bước 4. Cài đặt PySpark và thư viện hỗ trợ
# Cài đặt PySpark phiên bản tương ứng với Spark 3.4.4:

pip3 install pyspark==3.4.4

# Cài đặt thư viện cloudpickle phiên bản 1.6.0 để hỗ trợ serialization trong Spark:

pip3 install cloudpickle==1.6.0

## Chạy chương trình 
# Mở CMD, điều hướng đến thư mục chứa file personalized_pagerank.py
# Thực hiện lệnh sau để chạy chương trình:

python3 personalized_pagerank.py

## LƯU Ý:
Đảm bảo tất cả biến môi trường (JAVA_HOME, HADOOP_HOME, Path) được cập nhật sau mỗi bước.
Nếu gặp lỗi, kiểm tra lại đường dẫn hoặc chạy CMD với quyền quản trị.
Trước khi chạy nên khởi động chương trình trên môi trường máy ảo
