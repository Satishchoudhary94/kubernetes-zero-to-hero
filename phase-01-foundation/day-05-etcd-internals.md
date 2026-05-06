# Day 05 — etcd Internals — Raft, Backup, Restore

> **Phase:** 1 — Foundation | **Week:** Week 1 | **Time:** 4–5 hours

---

## 📚 Topics to Study

### 1. etcd Role in Kubernetes
- Only stateful component — lose etcd = lose cluster
- All cluster state stored as key-value pairs
- Only the API server talks to etcd directly
- Key structure: /registry/<resource>/<namespace>/<name>

### 2. Raft Consensus Algorithm
- Leader election: one leader, multiple followers
- Write quorum: majority must acknowledge before commit
- Why 3 or 5 nodes (never even numbers) for HA
- Split-brain scenario and why quorum prevents it
- Leader failover: election timeout, term increment

### 3. etcd Operations
- etcdctl commands: get, put, del, watch
- Authentication flags: --endpoints, --cacert, --cert, --key
- Compaction: remove old revisions to reclaim space
- Defragmentation: reclaim disk after compaction

### 4. etcd Backup and Restore (CKA Critical)
- etcdctl snapshot save <file>
- Verify snapshot: etcdctl snapshot status
- Restore: etcdctl snapshot restore + update static pod manifest
- What gets lost if restored from old snapshot

---

## 🔗 Docs & Resources

- [etcd official docs](https://etcd.io/docs/)
- [Kubernetes etcd backup](https://kubernetes.io/docs/tasks/administer-cluster/configure-upgrade-etcd/)
- [Raft visualization](https://raft.github.io/)

---

## 🧪 Hands-on Labs

- [ ] **Lab 1:** Connect to etcd using etcdctl and list all pod keys
- [ ] **Lab 2:** Read a specific pod's raw data from etcd
- [ ] **Lab 3:** Perform an etcd snapshot backup to `/tmp/etcd-backup.db`
- [ ] **Lab 4:** Verify the snapshot with `etcdctl snapshot status`
- [ ] **Lab 5:** Simulate a cluster state change, then restore from old snapshot
- [ ] **Lab 6:** Observe Raft leader election by stopping the leader

---

## 🐛 Production Issue to Debug
> After labs

- **PI-03:** etcd high latency causing API server timeouts — diagnose with etcdctl endpoint status

---

## ❓ Interview Questions
> Answer these in `my-notes/` after studying

1. What is the Raft consensus algorithm and why does etcd use it?
2. Why should etcd clusters always have an odd number of members?
3. What happens to running workloads if etcd goes down?
4. Walk me through the etcd backup and restore process.
5. What is etcd compaction and when should you run it?

---

## 📝 My Notes
> _Fill after studying_

---

## ✅ Completion Checklist

- [ ] Read all topics
- [ ] Completed all 6 labs
- [ ] Debugged PI-03
- [ ] Answered interview questions
- [ ] Notes written
