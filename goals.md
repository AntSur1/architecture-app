 # Toy social media clone — project checklist

Goal: a small social app (post, like, feed) running as multiple containers 
behind a load balancer, with a split database, deployed on AWS.

## 1. Core app (keep it small)
- [x] Decide the minimum feature set (sign up/log in, post, like, feed)
- [x] Pick a stack you're comfortable with
- [x] Decide how auth/sessions will work
- [ ] Get it running locally with a single database, no containers yet
- [ ] Confirm all core actions work end to end

## 2. Containerize it
- [ ] Write a Dockerfile for the app
- [ ] Get the app in a single container talking to a single Postgres container
- [ ] Set up Docker Compose so both start with one command
- [ ] Figure out how containers find each other (networking, service names)

## 3. Load balancing / routing
- [ ] Run 2-3 identical copies of the app container
- [ ] Add a reverse proxy in front (Nginx, or write your own)
- [ ] Get basic round-robin routing working
- [ ] Verify it — confirm requests land on different containers
- [ ] Optional: health checks — what happens if one container is down?

## 4. Database splitting
- [ ] Set up a primary + replica Postgres pair
- [ ] Get replication actually working
- [ ] Add routing logic: writes → primary, reads → replica
- [ ] Open question: what about reading your own write immediately after posting?
- [ ] Verify it — prove reads hit the replica, writes hit the primary

## 4b. Database backups
- [ ] Decide what "losing data" would mean for this app
- [ ] Get a basic manual backup working locally (dump to a file)
- [ ] Practice restoring from that backup
- [ ] Automate it onto a schedule
- [ ] Open question: where should backups live, and why does that matter?
- [ ] On AWS: check what's built into the managed DB vs what you still need yourself
- [ ] Optional: simulate a disaster and time your recovery

## 5. AWS deployment
- [ ] Get an AWS account set up (watch free tier limits)
- [ ] Learn just enough IAM to not lock yourself out
- [ ] Push Docker images somewhere AWS can pull from
- [ ] Get containers running on AWS instead of your laptop
- [ ] Move the database to an AWS-managed equivalent
- [ ] Put AWS's own load balancer in front
- [ ] Get a working public URL end to end
- [ ] Optional: check what logs/metrics AWS gives you for free

## 6. Stretch goals
- [ ] Infrastructure-as-code
- [ ] What would CI/CD do for this project?
- [ ] What happens under load, and how would you test that?
- [ ] Caching — where would it help?

## Notes
- Each section is independently demoable.
- Log what broke and why at each stage — that's your interview story later.


Your role is my mentor here. I want to do the decisins myself and i don't want you to solve or drive to fast forward.


I append this to all chats and do each decision/step in a separate chat. 

### Decisions
Features i will do:
* login/signup
* post
* feed
* like

Stack:
vanilla html + css -- frontend
fastapi -- backend
postgressql -- db
sqlalchemy -- db orm
alembic -- db migration
docker -- containerization
nginx -- reverse proxy
aws -- later

Auth:
