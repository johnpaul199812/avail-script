# Avail light node Monitoring Setup

Follow these steps to set up avail light node monitoring using the `avail.bash` script:

1. **Create the necessary files:**
    ```bash
    touch avail.bash
    touch avail_logs.txt
    ```

2. **Edit the `avail.bash` script:**
    - Open the `avail.bash` file for editing:
        ```bash
        nano avail.bash
        ```
    - Paste the following script into the file:
        ```bash
        #!/bin/bash

        while true; do
          echo "========== $(date) ==========" >> avail_logs.txt
          curl -sL1 http://avail.sh | bash >> avail_logs.txt 2>&1
          echo "Error: Light node panicked. Restarting..." >> avail_logs.txt
          sleep 10
        done
        ```
    - Save the file by pressing `Ctrl + O`, then `Enter`, and exit the editor by pressing `Ctrl + X`.

3. **Make the script executable:**
    ```bash
    chmod +x avail.bash
    ```

4. **Start a tmux session:**
    ```bash
    tmux new -t avail
    ```

5. **Run the script:**
    - Inside the tmux session, run the `avail.bash` script:
        ```bash
        ./avail.bash
        ```

6. **Detach from tmux:**
    - Detach from the tmux session by pressing `Ctrl + B`, then `D`.

7. **Monitor the logs:**
    - To monitor the logs, run the following command outside the tmux session:
        ```bash
        tail -f avail_logs.txt
        ```
    - This command will display the logs in real-time, allowing you to monitor the avail light node.
