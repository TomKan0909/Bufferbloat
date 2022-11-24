# Bufferbloat


## Questions 

1. *Why do you see a difference in webpage fetch times with small and large router buffers?* <br/> 
something bout large buffers getting clogged up causing RTT to increase thus webpage fetch time on avg higher for large buffer

2. *Bufferbloat can occur in other places such as your network interface card (NIC). Check the output of ifconfig eth0 on your VirtualBox VM. What is the (maximum) transmit queue length on the network interface reported by ifconfig? For this queue size and a draining rate of 100 Mbps, what is the maximum time a packet might wait in the queue before it leaves the NIC?* <br/>
MTU = 1500 B, Q_LEN = 1000
Total bits in queue = 1500 * 8 * 1000 = 12 * 10 ^6 b
time = (12 * 10^6 b) / (100 * 10^6 bps) = 1.2s

3. *How does the RTT reported by ping vary with the queue size? Write a symbolic equation to describe the relation between the two (ignore computation overheads in ping that might affect the final result).* <br/>
RTT ~ 0.01-0.03 * QUEUE_SIZE
0.62s / sz 20
1.28s/ sz 100

4. *Identify and describe two ways to mitigate the bufferbloat problem.* <br/>
- Use smarter deque techniques for buffer instead of FIFO, help smooth out network traffic instead of clumping it all together
- Decrease buffer size to help decrease buffer delay for packets. Let congestion control deal with packet loss issue