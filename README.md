# React-and-Git-Command-Note
//gitlab cmd
- git clone https://gitlab.com/aakasd/project.git
- git clone -b <branchname> <remote-repo-url>
- git checkout -b aakash
- git checkout origin/aakash
- git branch
- git branch -r
- git remote -v
- git push
- git push -uf origin aakash
- git pull origin main --ff
- git branch --delete <branch>
git config
-git config --global user.email aakashdeep983@gmail.com
-git config --global user.name aakash983

- git status
- git add .
- git commit -m "message"
-git push
-npm config set legacy-peer-deps true
-npm install --legacy-peer-deps
git push REMOTE-NAME BRANCH-NAME

Thumb rule of git commit 
1. stash ur changes
2. take a pull
3. apply ur's changes
4.resolve any merge confilcts is there then commit
5. commmit ur changes
6. push the changes and raised pr

//node version- nvm
- nvm list
- nvm install v16.0.0
- nvm use v16.0.0
- nvm -v
- //@ts-ignore

//react node
- node -v
- npx create-react-app my-app --template typescript
- npm install --save typescript @types/node @types/react @types/react-dom @types/jest
- npm install typescript@latest --save-dev
- npx create-react-app name

- code .
- npm install /npm start
- rm -r node_modules
- rm -rf node_modules
- rm -f package-lock.json
- npm cache clean --force
- npm audit fix --force 
- npm set audit false
- --legacy-peer-deps
-npm init
- rafce
- ctrl+d bscp
  
//Json-server react
- npm install Json-server 
- json-server –watch db.json 
- npm install -g json-server

//react-hooks basic
import "./styles.css";
import React, {
  useState,
  useEffect,
  useRef,
  useMemo,
  useCallback,
} from "react";

const App = () => {
  //usestate(state hooks)
  const [count, setCount] = useState(0);
  const increment = () => {
    setCount(count + 1);
  };
  const decrement = () => {
    setCount(count - 1);
  };
  //useEffect(state hooks)
  const [data, setData] = useState(null);
  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/todos/1")
      .then((response) => response.json())
      .then((result) => {
        setData(result.title);
      })
      .catch((error) => {
        console.error("Error Fetching Data", error);
      });
    //   setTimeout(() => {
    //     setCount((count) => count + 1);
    //   }, 1000);
    return () => {};
  }, []);
  // useRef(state hooks)
  const inputRef = useRef(null);
  const handleRef = () => {
    inputRef.current.focus();
  };

  //useMemo(state hooks)
  const doubleCount = useMemo(() => {
    return count * 2;
  }, [count]);

  //Callback(state hooks)
  const callbackIncrement = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return (
    <div className="App">
      <ul>
        Hooks :-
        <h4>First- State Hook</h4>
        <hr />
        <li>
          <h4> 1- UseState[State Hook] </h4>
          <button onClick={decrement}>-</button>
          <p style={{ color: "red" }}>Count:({count})</p>
          <button onClick={increment}>+</button>
        </li>
        <hr />
        {data ? (
          <div>
            <h4>2- UseEffect[State Hook] Fetch Data:</h4>
            <span style={{ color: "red" }}>{data}</span>
          </div>
        ) : (
          <p>Loading Data...</p>
        )}
        <hr />
        <div>
          <h4>3- UseRef[State Hook]</h4>
          <input type="text" ref={inputRef} style={{ color: "red" }} />
          <button onClick={handleRef}>Focus Input</button>
        </div>
        <hr />
        <div>
          <h4>4- UseMemo[State Hook]</h4>
          <p style={{ color: "red" }}>Count: {count}</p>
          <p style={{ color: "red" }}>Double Count: {doubleCount}</p>
          <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
        <hr />
        <div>
          <h4>5- Callback [State Hook]</h4>
          <p style={{ color: "red" }}>Count: {count}</p>
          <button onClick={increment}>Increment</button>
        </div>
        <hr />
        <div>
          <h4>6- useReducer [State Hook]</h4>
        </div>
        <hr />
      </ul>
    </div>
  );
};
export default App;

//aws process

-create New S3 bucket
-Upload the build file
-follow the step to configure
[
Permissions overview
Access
Public

Block public access (bucket settings)
Block all public access
 Off
Individual Block Public Access settings for this bucket

Bucket policy

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicRead",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::facilitator-dev.pi-play.com/*"
        }
    ]
}

Object OwnershipInfo
Object Ownership
Bucket owner enforced
ACLs are disabled. All objects in this bucket are owned by this account. Access to this bucket and its objects is specified using only policies.

Access control list (ACL)

Bucket owner (your AWS account)

Canonical ID:
908f113eeecd0664379db49b4fd3a5b8f196e7e83554dc89e89cdfe597cfba64

List, Write

Read, Write

Everyone (public access)

Group:
http://acs.amazonaws.com/groups/global/AllUsers

-

-

Authenticated users group (anyone with an AWS account)

Group:
http://acs.amazonaws.com/groups/global/AuthenticatedUsers

-

-

S3 log delivery group

Group:
http://acs.amazonaws.com/groups/s3/LogDelivery


properties overview

Bucket Versioning
Bucket Versioning
Disabled
Multi-factor authentication (MFA) delete
An additional layer of security that requires multi-factor authentication for changing Bucket Versioning settings and permanently deleting object versions. To modify MFA delete settings, use the AWS CLI, AWS SDK, or the Amazon S3 REST API. Learn more 
Disabled

Default encryptionInfo
Server-side encryption is automatically applied to new objects stored in this bucket.

Edit
Encryption typeInfo
Server-side encryption with Amazon S3 managed keys (SSE-S3)

Bucket Key
When KMS encryption is used to encrypt new objects in this bucket, the bucket key reduces encryption costs by lowering calls to AWS KMS. Learn more 
Enabled

Server access logging
Disabled

Send notifications to Amazon EventBridge for all events in this bucket
Off

Transfer acceleration
Disabled

Object Lock
Disabled

Requester pays
Disabled

Static website hosting
Enabled
Hosting type
Bucket hosting
Bucket website endpoint
]
