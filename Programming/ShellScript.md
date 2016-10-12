# Format date string

    date +%Y-%m-%d:%H:%M:%S

See details on <http://stackoverflow.com/questions/1401482/yyyy-mm-dd-format-date-in-shell-script>

# For loop


    #!/bin/bash
    for i in {1..5}
    do
       echo "Welcome $i times"
    done

See details on <http://www.cyberciti.biz/faq/bash-for-loop/>.

# multi-thread

    <command> &
    <command> &
    <command> &
    wait

See detail on <http://stackoverflow.com/questions/2425870/multithreading-in-bash>.

# Getting host IP address

    ifconfig | grep -Eo 'inet (addr:)?([0-9]*\.){3}[0-9]*' | grep -Eo '([0-9]*\.){3}[0-9]*' | grep -v '127.0.0.1'

See details on <http://stackoverflow.com/questions/13322485/how-to-i-get-the-primary-ip-address-of-the-local-machine-on-linux-and-os-x>.

# Pause

    read -p "Press [Enter] key to start backup..."

See details on <http://www.cyberciti.biz/tips/linux-unix-pause-command.html>.
