# EBS vs Instance Store 

## What is Instance Store

- `Many Amazon EC2 instance types can access disk storage from disks that are physically attached to the host computer. This disk storage is referred to as instance store.`
- Instance store are provided free. You only pay for EC2 Instance hours.
- [See Docs for details](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html)

Instances can be either EBS backed or Instance store backed ("Backed" refers to where the boot device is).

- From Instane Store Docs: `Instance store volumes are ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content, or for data that is replicated across a fleet of instances, such as a load-balanced pool of web servers.`
- Also from Docs: `If you require greater flexibility in latency or throughput, we recommend using Amazon EBS.`
- Be aware common instance types t2.micro, t2.small, t2.medium don't provide instance store, making it less flexible.
- Some people argue instance store provides better performance.

External Links:
- [You Should Use EBS Boot Instances on Amazon EC2](http://alestic.com/2012/01/ec2-ebs-boot-recommended)
- [Stackoverflow: Benefits of EBS vs. instance-store (and vice-versa)](http://stackoverflow.com/questions/3630506/benefits-of-ebs-vs-instance-store-and-vice-versa)

As a conclusion, depending on your use case, try and see for yourself.