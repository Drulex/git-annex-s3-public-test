# git-annex-s3-public-test
Testing git-annex with S3 for public reads and private writes


## steps to start tracking large files (developer workflow)

```
# export AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY. Generated via AWS control panel

git annex init

# init the s3 remote with public and publicurl which sets the ACL on the bucket automatically for public reads/private writes
git annex initremote s3 type=S3 bucket="drulex.test.neuropoly.001" encryption=none public=yes publicurl=http://drulex.test.neuropoly.001.s3.amazonaws.com

# add a big file and send it to s3
git annex add big-file.iso
git annex copy big-file.iso --to s3

# alternatively copy to all remotes
# git annex synx --content

# sync metadata with other remotes
git annex sync


# steps to retrieve large files (user workflow)

# enable the repo
git annex enableremote s3

# retrieve a specific file
git annex get big-file.iso

# alternatively retrieve all files
# git annex get
```
