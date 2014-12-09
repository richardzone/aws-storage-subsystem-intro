# EBS Performance

It's better to use EBS-Optimized EC2 Instances with EBS when you're optimizing performance.

## Pre-Warming EBS Volumes

- 5 to 50 percent loss of IOPS for your volume the first time each block is accessed
- AWS suggests for most applications, amortizing this cost over the lifetime of the volume is acceptable.
- Details can be found at [Pre-Warming Amazon EBS Volumes](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-prewarm.html)

## EBS IOPS Charactistics

- IOPS are input/output operations per second.
- I/O operations larger than 256 KB are counted in 256 KB capacity units.
- Volume Throughtput Limit: 128MB/s

## Create EBS Volumn from snapshots

- New volumes are created lazily in background, and can be used RIGHT AWAY
- If your instance accesses a piece of data that hasn't yet been loaded, the volume immediately downloads the requested data from Amazon S3, and then continues loading the rest of the volume’s data in the background.
