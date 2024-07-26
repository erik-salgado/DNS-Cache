# Local DNS Cache Exercise

- Go to DC-1 and change mainframe's record address to 8.8.8.8.
![Screenshot 2024-07-09 202530](https://github.com/user-attachments/assets/c6c16fee-d0ea-4b9c-9a31-c6957f253510)
![Screenshot 2024-07-09 202539](https://github.com/user-attachments/assets/6685b3dc-025d-4c77-80f9-fd8a455fcab4)

- Go back to Client-1 and ping "mainframe". Notice that even though we've changed the IP address to 8.8.8.8, its still pinging the old address. The reason for this is because this still exists in the local DNS cache on this computer.
![Screenshot 2024-07-09 202640](https://github.com/user-attachments/assets/34643200-4f5c-4755-a22a-d1316dbe4210)

- If you type "nslookup mainframe" it will have the same old IP address
![Screenshot 2024-07-09 202746](https://github.com/user-attachments/assets/b39c3c5c-b801-4a40-9d6b-bc04de4c46f4)

- This is where the command DNS FLUSH comes into play. Sometimes a network resource IP address might change, but your local computer still has the old IP address cached and this could cause you to not reach out certain resources. So oftentime in troubleshooting we use the command dns flush to wipe out all of the cache and lets it get repopulated by a querying DNS server. You need to open command prompt as an admin in order to do this, type "ipconfig /flushdns"

![Screenshot 2024-07-09 202846](https://github.com/user-attachments/assets/6703bdaa-f209-4309-9728-50fbbfbbe9ec)
![Screenshot 2024-07-09 203045](https://github.com/user-attachments/assets/2ce5b5a6-ef5d-4509-a607-ca2640dd89d0)

- Type "ipconfig /displaydns" command and notice that it's empty, thats because we flush all the dns that was there.
![Screenshot 2024-07-09 203205](https://github.com/user-attachments/assets/9e475f86-7848-4adf-b6c6-300c3573add3)

- Ping "mainframe". So now this is what's happening in the background. The computer will search the local DNS cache but it wll be empty because of the flush dns command, it will then go to the DNS server, and since we've updated the records on the DNS server, it will put the latest record. So after pinging "mainframe" it will resolve it to 8.8.8.8
![Screenshot 2024-07-09 203223](https://github.com/user-attachments/assets/71e560e0-a8ce-43dc-8a91-89b5841bd4ad)

- If you type "ipconfig/ displaydns" it will show the latest record there is
![Screenshot 2024-07-09 203244](https://github.com/user-attachments/assets/af72fd97-4484-4053-9fc3-0f83a14bde15)

This brings us the conclusion for this exercise. Thank you for watching! :)
