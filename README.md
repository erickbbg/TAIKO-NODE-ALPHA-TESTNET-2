# TAIKO-NODE-ALPHA-TESTNET-2
*Taiko là blockchain layer2 xây dựng dựa trên công nghệ zkEVM tương thích hoàn toàn với Ethereum (Fully Ethereum-equivalent ZK-Rollup). Taiko hiện là Layer 2 đi theo hướng Type 1 ZK-EVM, đây cũng là type có cấp độ tương thích với EVM cao nhất*



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

```
sudo apt update && sudo apt install git && sudo apt install apt-transport-https ca-certificates software-properties-common curl

sudo curl -f -s -S -L https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"

d /root

sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

Kiểm tra trạng thái của Docker:

```
sudo systemctl status docker
```

# Các bước chạy Node Taiko

**1. Sao chép đơn giản Node**

```
git clone https://github.com/taikoxyz/simple-taiko-node.git

cd simple-taiko-node
```

**2. Cấu hình Node**

Đầu tiên, sao chép `.env.sample` vào một tệp tin mới `.env`:

```
cp .env.sample .env
```

Tiếp theo, mở tệp `.env`

```
nano .env
```

**3. Xác minh trở thành Prover**

Sử dụng  Alchemy hoặc Infura để nhận được `ENDPOINT`. Đảm bảo rằng bạn chọn `RPC` là `Sepolia testnet` chứ không phải `Ethereum mainnet`

- L1_ENDPOINT_HTTP="..."
- L1_ENDPOINT_WS="..."

![image](https://user-images.githubusercontent.com/108129127/228375928-30004e82-7d00-41cf-93d6-d0ab5d052ee6.png)

Tiếp theo, Đặt `ENABLE_PROVER=true` (thay thế mặc định `false` bằng `true`). Ở `L1_PROVER_PRIVATE_KEY` nhập ví metamask của bạn vào:

```
L1_PROVER_PRIVATE_KEY="Coppy private key ví metamask của bạn vào đây"
```

