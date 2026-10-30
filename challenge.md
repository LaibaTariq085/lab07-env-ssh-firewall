PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/home/laibatariq085
LANG=en_US.UTF-8
PWD=/home/laibatariq085/lab07-env-ssh-firewall

JOB 4: Block Ping and Allow Ping Again

1. First check ping:
ping 192.168.202.129

2. Backup UFW rules:
sudo cp /etc/ufw/before.rules ~/before.rules.backup

3. Block incoming ping by changing ACCEPT to DROP:
sudo sed -i '/echo-request/s/ACCEPT/DROP/' /etc/ufw/before.rules

4. Reload firewall:
sudo ufw reload

5. Test ping from Windows CMD:
ping -n 4 192.168.202.129
Expected result: Request timed out.

6. Allow ping again:
sudo sed -i '/echo-request/s/DROP/ACCEPT/' /etc/ufw/before.rules

7. Reload firewall again:
sudo ufw reload

8. Test ping again from Windows CMD:
ping -n 4 192.168.202.129
Expected result: Reply from 192.168.202.129

JOB 2: Temporary Student Environment Variables

1. Set temporary variables:
export STUDENT_NAME="Laiba"
export STUDENT_ROLL_NUMBER="FA24B1-SE-085"
export STUDENT_SEMESTER="Fifth"

2. Display the variables:
printenv | grep '^STUDENT_'

3. Exit SSH and reconnect to check temporary variables:
printenv | grep '^STUDENT_'

Expected result: No output after reconnect because temporary variables disappear.

JOB 3: Permanent Student Environment Variables

1. Add the following variables to ~/.bashrc:
export STUDENT_NAME="Laiba"
export STUDENT_ROLL_NUMBER="FA24B1-SE-085"
export STUDENT_SEMESTER="Fifth"

2. Apply changes:
source ~/.bashrc

3. Display variables:
printenv | grep '^STUDENT_'

Expected result: All three student variables should be displayed.

4. Reconnect to Ubuntu and check again:
printenv | grep '^STUDENT_'

Expected result: All three variables should still be displayed after reconnect.
