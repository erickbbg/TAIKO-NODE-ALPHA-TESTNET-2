# TAIKO-NODE-ALPHA-TESTNET-2
**Taiko là blockchain layer2 xây dựng dựa trên công nghệ zkEVM tương thích hoàn toàn với Ethereum (Fully Ethereum-equivalent ZK-Rollup). Taiko hiện là Layer 2 đi theo hướng Type 1 ZK-EVM, đây cũng là type có cấp độ tương thích với EVM cao nhất
**

**Cơ chế hoạt động của Taiko Protocol**

Để hiểu rõ về cơ chế hoạt động của Taiko, trước tiên cần biết về các đối tượng tham gia trong Taiko, cụ thể: 

- **Propose**r: Đảm nhiệm việc tạo khối từ cho giao dịch của người dùng từ L2 và đề xuất các khối này đến L1. 

- **Prover**: Có trách nhiệm tạo ra chứng minh ZK-SNARK để kiểm tra tính hợp lệ của giao dịch từ L2 và các khối mà Proposer đã đề xuất. 

- **Node Runner**: Đảm nhiệm việc thực thi giao dịch trong mạng lưới. Proposer và Prover cũng bắt buộc chạy node để đáp ứng vai trò của họ trong mạng lưới. 


Từ các thành phần tham gia trên, luồng xác nhận giao dịch của Taiko sẽ được thực hiện như sau: 

- Người dùng thực hiện giao dịch trên L2 (Taiko)

- Đề xuất khối (propose): Proposer tạo các khối Rollup tổng hợp các giao dịch từ người dùng ở L2 và đề xuất chúng lên Ethereum. 

- Tạo bằng chứng (prove): Các Prover sẽ bắt đầu tạo bằng chứng hợp lệ và chứng minh tính đúng đắn của các khối vừa được gửi lên. 

- Xác thực (verify): Sau khi Prover đã chứng minh được tính đúng đắn cho khối và khối trước nó, chúng sẽ đánh dấu khối là đã hoàn thành trên chain (proved → verified và chuyển trạng thái từ xanh lá sang vàng) 

# Cấu hình tham gia Testnet-Alpha 2

**Tối thiểu:**

- CPU 2+ Cores
- 4GB RAM
- 1TB 
- 8 MBit/s

**Đề xuất**

- CPU 4+ cores
- 16GB+ RAM
- SSD 1TB 
- 25+ MBit/s

# Hướng dẫn chạy Node Taiko

1. Cập nhật hệ thống

</sudo apt update && sudo apt install git && sudo apt install apt-transport-https ca-certificates software-properties-common curl> 
