Using Fdisk (Beyond fdisk -l)
============================

* Besides being a great tool to list your partions, fdisk can also be used to format drives:

    - Choose the drive that you want to format `fdisk /dev/sda`

    - Use the `p` key to display the disk's current partition configuration

    - The `g` key instantly removes all existing disk partitions and creates a new GPT disklabel

    - The `d` key schedules a partition for deletion until 

    - `n` creates a new partition, followed by `1` to select the first partition


