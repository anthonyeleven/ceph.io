---
title: "v12.2.2 Luminous released"
date: "2017-12-01"
author: "TheAnalyst"
tags:
  - "release"
  - "luminous"
---

This is the second bugfix release of Luminous v12.2.x long term stable release series. It contains a range of bug fixes and a few features across Bluestore, CephFS, RBD & RGW. We recommend all the users of 12.2.x series update.

For more detailed information, see [`the complete changelog`](http://docs.ceph.com/ceph-prs/19264/_downloads/v12.2.2.txt).

### Notable Changes

- Standby ceph-mgr daemons now redirect requests to the active messenger, easing configuration for tools & users accessing the web dashboard, restful API, or other ceph-mgr module services.
- The prometheus module has several significant updates and improvements.
- The new balancer module enables automatic optimization of CRUSH weights to balance data across the cluster.
- The ceph-volume tool has been updated to include support for BlueStore as well as FileStore. The only major missing ceph-volume feature is dm-crypt support.
- RGW’s dynamic bucket index resharding is disabled in multisite environments, as it can cause inconsistencies in replication of bucket indexes to remote sites.

### Other Notable Changes

- build/ops: bump sphinx to 1.6 ([issue#21717](http://tracker.ceph.com/issues/21717), [pr#18167](https://github.com/ceph/ceph/pull/18167), Kefu Chai, Alfredo Deza)
- build/ops: macros expanding in spec file comment ([issue#22250](http://tracker.ceph.com/issues/22250), [pr#19173](https://github.com/ceph/ceph/pull/19173), Ken Dreyer)
- build/ops: python-numpy-devel build dependency for SUSE ([issue#21176](http://tracker.ceph.com/issues/21176), [pr#17692](https://github.com/ceph/ceph/pull/17692), Nathan Cutler)
- build/ops: selinux: Allow getattr on lnk sysfs files ([issue#21492](http://tracker.ceph.com/issues/21492), [pr#18650](https://github.com/ceph/ceph/pull/18650), Boris Ranto)
- build/ops: Ubuntu amd64 client can not discover the ubuntu arm64 ceph cluster ([issue#19705](http://tracker.ceph.com/issues/19705), [pr#18293](https://github.com/ceph/ceph/pull/18293), Kefu Chai)
- core: buffer: fix ABI breakage by removing list \_mempool member ([issue#21573](http://tracker.ceph.com/issues/21573), [pr#18491](https://github.com/ceph/ceph/pull/18491), Sage Weil)
- core: Daemons(OSD, Mon…) exit abnormally at injectargs command ([issue#21365](http://tracker.ceph.com/issues/21365), [pr#17864](https://github.com/ceph/ceph/pull/17864), Yan Jun)
- core: Disable messenger logging (debug ms = 0/0) for clients unless overridden ([issue#21860](http://tracker.ceph.com/issues/21860), [pr#18529](https://github.com/ceph/ceph/pull/18529), Jason Dillaman)
- core: Improve OSD startup time by only scanning for omap corruption once ([issue#21328](http://tracker.ceph.com/issues/21328), [pr#17889](https://github.com/ceph/ceph/pull/17889), Luo Kexue, David Zafman)
- core: upmap does not respect osd reweights ([issue#21538](http://tracker.ceph.com/issues/21538), [pr#18699](https://github.com/ceph/ceph/pull/18699), Theofilos Mouratidis)
- dashboard: barfs on nulls where it expects numbers ([issue#21570](http://tracker.ceph.com/issues/21570), [pr#18728](https://github.com/ceph/ceph/pull/18728), John Spray)
- dashboard: OSD list has servers and osds in arbitrary order ([issue#21572](http://tracker.ceph.com/issues/21572), [pr#18736](https://github.com/ceph/ceph/pull/18736), John Spray)
- dashboard: the dashboard uses absolute links for filesystems and clients ([issue#20568](http://tracker.ceph.com/issues/20568), [pr#18737](https://github.com/ceph/ceph/pull/18737), Nick Erdmann)
- filestore: set default readahead and compaction threads for rocksdb ([issue#21505](http://tracker.ceph.com/issues/21505), [pr#18234](https://github.com/ceph/ceph/pull/18234), Josh Durgin, Mark Nelson)
- librbd: object map batch update might cause OSD suicide timeout ([issue#21797](http://tracker.ceph.com/issues/21797), [pr#18416](https://github.com/ceph/ceph/pull/18416), Jason Dillaman)
- librbd: snapshots should be created/removed against data pool ([issue#21567](http://tracker.ceph.com/issues/21567), [pr#18336](https://github.com/ceph/ceph/pull/18336), Jason Dillaman)
- mds: make sure snap inode’s last matches its parent dentry’s last ([issue#21337](http://tracker.ceph.com/issues/21337), [pr#17994](https://github.com/ceph/ceph/pull/17994), “Yan, Zheng”)
- mds: sanitize mdsmap of removed pools ([issue#21945](http://tracker.ceph.com/issues/21945), [issue#21568](http://tracker.ceph.com/issues/21568), [pr#18628](https://github.com/ceph/ceph/pull/18628), Patrick Donnelly)
- mgr: bulk backport of ceph-mgr improvements ([issue#21594](http://tracker.ceph.com/issues/21594), [issue#17460](http://tracker.ceph.com/issues/17460), [issue#21197](http://tracker.ceph.com/issues/21197), [issue#21158](http://tracker.ceph.com/issues/21158), [issue#21593](http://tracker.ceph.com/issues/21593), [pr#18675](https://github.com/ceph/ceph/pull/18675), Benjeman Meekhof, Sage Weil, Jan Fajerski, John Spray, Kefu Chai, My Do, Spandan Kumar Sahu)
- mgr: ceph-mgr gets process called “exe” after respawn ([issue#21404](http://tracker.ceph.com/issues/21404), [pr#18738](https://github.com/ceph/ceph/pull/18738), John Spray)
- mgr: fix crashable DaemonStateIndex::get calls ([issue#17737](http://tracker.ceph.com/issues/17737), [pr#18412](https://github.com/ceph/ceph/pull/18412), John Spray)
- mgr: key mismatch for mgr after upgrade from jewel to luminous(dev) ([issue#20950](http://tracker.ceph.com/issues/20950), [pr#18727](https://github.com/ceph/ceph/pull/18727), John Spray)
- mgr: mgr status module uses base 10 units ([issue#21189](http://tracker.ceph.com/issues/21189), [issue#21752](http://tracker.ceph.com/issues/21752), [pr#18257](https://github.com/ceph/ceph/pull/18257), John Spray, Yanhu Cao)
- mgr: mgr\[zabbix\] float division by zero ([issue#21518](http://tracker.ceph.com/issues/21518), [pr#18734](https://github.com/ceph/ceph/pull/18734), John Spray)
- mgr: Prometheus crash when update ([issue#21253](http://tracker.ceph.com/issues/21253), [pr#17867](https://github.com/ceph/ceph/pull/17867), John Spray)
- mgr: prometheus module generates invalid output when counter names contain non-alphanum characters ([issue#20899](http://tracker.ceph.com/issues/20899), [pr#17868](https://github.com/ceph/ceph/pull/17868), John Spray, Jeremy H Austin)
- mgr: Quieten scary RuntimeError from restful module on startup ([issue#21292](http://tracker.ceph.com/issues/21292), [pr#17866](https://github.com/ceph/ceph/pull/17866), John Spray)
- mgr: Spurious ceph-mgr failovers during mon elections ([issue#20629](http://tracker.ceph.com/issues/20629), [pr#18726](https://github.com/ceph/ceph/pull/18726), John Spray)
- mon: Client client.admin marked osd.2 out, after it was down for 1504627577 seconds ([issue#21249](http://tracker.ceph.com/issues/21249), [pr#17862](https://github.com/ceph/ceph/pull/17862), John Spray)
- mon: DNS SRV default service name not used anymore ([issue#21204](http://tracker.ceph.com/issues/21204), [pr#17863](https://github.com/ceph/ceph/pull/17863), Kefu Chai)
- mon/MgrMonitor: handle cmd descs to/from disk in the absence of active mgr ([issue#21300](http://tracker.ceph.com/issues/21300), [pr#18038](https://github.com/ceph/ceph/pull/18038), Joao Eduardo Luis)
- mon/mgr: sync “mgr\_command\_descs”,”osd\_metadata” and “mgr\_metadata” prefixes to new mons ([issue#21527](http://tracker.ceph.com/issues/21527), [pr#18620](https://github.com/ceph/ceph/pull/18620), huanwen ren)
- mon: osd feature checks with 0 up osds ([issue#21471](http://tracker.ceph.com/issues/21471), [issue#20751](http://tracker.ceph.com/issues/20751), [pr#18364](https://github.com/ceph/ceph/pull/18364), Brad Hubbard, Sage Weil)
- mon,osd: fix “pg ls {forced\_backfill, backfilling}” ([issue#21609](http://tracker.ceph.com/issues/21609), [pr#18236](https://github.com/ceph/ceph/pull/18236), Kefu Chai)
- mon/OSDMonitor: add option to fix up ruleset-\* to crush-\* for ec profiles ([issue#22128](http://tracker.ceph.com/issues/22128), [pr#18945](https://github.com/ceph/ceph/pull/18945), Sage Weil)
- mon, osd: per pool space-full flag support ([issue#21409](http://tracker.ceph.com/issues/21409), [pr#17730](https://github.com/ceph/ceph/pull/17730), xie xingguo)
- mon/PGMap: Fix %USED calculation ([issue#22247](http://tracker.ceph.com/issues/22247), [pr#19230](https://github.com/ceph/ceph/pull/19230), Xiaoxi Chen)
- mon: update get\_store\_prefixes implementations ([issue#21534](http://tracker.ceph.com/issues/21534), [pr#18621](https://github.com/ceph/ceph/pull/18621), John Spray, huanwen ren)
- msgr: messages/MOSDMap: do compat reencode of crush map, too ([issue#21882](http://tracker.ceph.com/issues/21882), [pr#18456](https://github.com/ceph/ceph/pull/18456), Sage Weil)
- msgr: src/messages/MOSDMap: reencode OSDMap for older clients ([issue#21660](http://tracker.ceph.com/issues/21660), [pr#18140](https://github.com/ceph/ceph/pull/18140), Sage Weil)
- os/bluestore/BlueFS: fix race with log flush during async log compaction ([issue#21878](http://tracker.ceph.com/issues/21878), [pr#18503](https://github.com/ceph/ceph/pull/18503), Sage Weil)
- os/bluestore: fix another aio stall/deadlock ([issue#21470](http://tracker.ceph.com/issues/21470), [pr#18127](https://github.com/ceph/ceph/pull/18127), Sage Weil)
- os/bluestore: fix SharedBlob unregistration ([issue#22039](http://tracker.ceph.com/issues/22039), [pr#18983](https://github.com/ceph/ceph/pull/18983), Sage Weil)
- os/bluestore: handle compressed extents in blob unsharing checks ([issue#21766](http://tracker.ceph.com/issues/21766), [pr#18501](https://github.com/ceph/ceph/pull/18501), Sage Weil)
- os/bluestore: replace 21089 repair with something online (instead of fsck) ([issue#21089](http://tracker.ceph.com/issues/21089), [pr#17734](https://github.com/ceph/ceph/pull/17734), Sage Weil)
- os/bluestore: set bitmap freelist resolution to min\_alloc\_size ([issue#21408](http://tracker.ceph.com/issues/21408), [pr#18050](https://github.com/ceph/ceph/pull/18050), Sage Weil)
- os/blueStore::umount will crash when the BlueStore is opened by start\_kv\_only() ([issue#21624](http://tracker.ceph.com/issues/21624), [pr#18750](https://github.com/ceph/ceph/pull/18750), Chang Liu)
- osd: additional protection for out-of-bounds EC reads ([issue#21629](http://tracker.ceph.com/issues/21629), [pr#18413](https://github.com/ceph/ceph/pull/18413), Jason Dillaman)
- osd: allow recovery preemption ([issue#21613](http://tracker.ceph.com/issues/21613), [pr#18025](https://github.com/ceph/ceph/pull/18025), Sage Weil)
- osd: build\_past\_intervals\_parallel: Ignore new partially created PGs ([issue#21833](http://tracker.ceph.com/issues/21833), [pr#18673](https://github.com/ceph/ceph/pull/18673), David Zafman)
- osd: dump bluestore debug on shutdown if debug option is set ([issue#21259](http://tracker.ceph.com/issues/21259), [pr#18103](https://github.com/ceph/ceph/pull/18103), Sage Weil)
- osd: make stat\_bytes and stat\_bytes\_used counters PRIO\_USEFUL ([issue#21981](http://tracker.ceph.com/issues/21981), [pr#18723](https://github.com/ceph/ceph/pull/18723), Yao Zongyou)
- osd: make the PG’s SORTBITWISE assert a more generous shutdown ([issue#20416](http://tracker.ceph.com/issues/20416), [pr#18132](https://github.com/ceph/ceph/pull/18132), Greg Farnum)
- osd: OSD metadata ‘backend\_filestore\_dev\_node’ is unknown even for simple deployment ([issue#20944](http://tracker.ceph.com/issues/20944), [pr#17865](https://github.com/ceph/ceph/pull/17865), Sage Weil)
- rbd: \[cli\] mirror getter commands will fail if mirroring has never been enabled ([issue#21319](http://tracker.ceph.com/issues/21319), [pr#17861](https://github.com/ceph/ceph/pull/17861), Jason Dillaman)
- rbd: cls/journal: fixed possible infinite loop in expire\_tags ([issue#21956](http://tracker.ceph.com/issues/21956), [pr#18626](https://github.com/ceph/ceph/pull/18626), Jason Dillaman)
- rbd: cls/journal: possible infinite loop within tag\_list class method ([issue#21771](http://tracker.ceph.com/issues/21771), [pr#18417](https://github.com/ceph/ceph/pull/18417), Jason Dillaman)
- rbd: \[rbd-mirror\] asok hook names not updated when image is renamed ([issue#20860](http://tracker.ceph.com/issues/20860), [pr#17860](https://github.com/ceph/ceph/pull/17860), Mykola Golub)
- rbd: \[rbd-mirror\] forced promotion can result in incorrect status ([issue#21559](http://tracker.ceph.com/issues/21559), [pr#18337](https://github.com/ceph/ceph/pull/18337), Jason Dillaman)
- rbd: \[rbd-mirror\] peer cluster connections should filter out command line optionals ([issue#21894](http://tracker.ceph.com/issues/21894), [pr#18566](https://github.com/ceph/ceph/pull/18566), Jason Dillaman)
- rgw: add support for Swift’s per storage policy statistics ([issue#17932](http://tracker.ceph.com/issues/17932), [issue#21506](http://tracker.ceph.com/issues/21506), [pr#17835](https://github.com/ceph/ceph/pull/17835), Radoslaw Zarzynski, Casey Bodley)
- rgw: add support for Swift’s reversed account listings ([issue#21148](http://tracker.ceph.com/issues/21148), [pr#17834](https://github.com/ceph/ceph/pull/17834), Radoslaw Zarzynski)
- rgw: avoid logging keystone revocation failures when no keystone is configured ([issue#21400](http://tracker.ceph.com/issues/21400), [pr#18441](https://github.com/ceph/ceph/pull/18441), Abhishek Lekshmanan)
- rgw: disable dynamic resharding in multisite enviorment ([issue#21725](http://tracker.ceph.com/issues/21725), [pr#18432](https://github.com/ceph/ceph/pull/18432), Orit Wasserman)
- rgw: encryption: PutObj response does not include sse-kms headers ([issue#21576](http://tracker.ceph.com/issues/21576), [pr#18442](https://github.com/ceph/ceph/pull/18442), Casey Bodley)
- rgw: encryption: reject requests that don’t provide all expected headers ([issue#21581](http://tracker.ceph.com/issues/21581), [pr#18429](https://github.com/ceph/ceph/pull/18429), Enming Zhang)
- rgw: expose –sync-stats via admin api ([issue#21301](http://tracker.ceph.com/issues/21301), [pr#18439](https://github.com/ceph/ceph/pull/18439), Nathan Johnson)
- rgw: failed CompleteMultipartUpload request does not release lock ([issue#21596](http://tracker.ceph.com/issues/21596), [pr#18430](https://github.com/ceph/ceph/pull/18430), Matt Benjamin)
- rgw\_file: set s->obj\_size from bytes\_written ([issue#21940](http://tracker.ceph.com/issues/21940), [pr#18599](https://github.com/ceph/ceph/pull/18599), Matt Benjamin)
- rgw: fix a bug about inconsistent unit of comparison ([issue#21590](http://tracker.ceph.com/issues/21590), [pr#18438](https://github.com/ceph/ceph/pull/18438), gaosibei)
- rgw: fix bilog entries on multipart complete ([issue#21772](http://tracker.ceph.com/issues/21772), [pr#18334](https://github.com/ceph/ceph/pull/18334), Casey Bodley)
- rgw: fix error handling in ListBucketIndexesCR ([issue#21735](http://tracker.ceph.com/issues/21735), [pr#18591](https://github.com/ceph/ceph/pull/18591), Casey Bodley)
- rgw: fix refcnt issues ([issue#21819](http://tracker.ceph.com/issues/21819), [pr#18539](https://github.com/ceph/ceph/pull/18539), baixueyu)
- rgw: lc process only schdule the first item of lc objects ([issue#21022](http://tracker.ceph.com/issues/21022), [pr#17859](https://github.com/ceph/ceph/pull/17859), Shasha Lu)
- rgw: list bucket which enable versioning get wrong result when user marker ([issue#21500](http://tracker.ceph.com/issues/21500), [pr#18569](https://github.com/ceph/ceph/pull/18569), yuliyang)
- rgw: list\_objects() honors end\_marker regardless of namespace ([issue#18977](http://tracker.ceph.com/issues/18977), [pr#17832](https://github.com/ceph/ceph/pull/17832), Radoslaw Zarzynski)
- rgw: Multipart upload may double the quota ([issue#21586](http://tracker.ceph.com/issues/21586), [pr#18435](https://github.com/ceph/ceph/pull/18435), Sibei Gao)
- rgw: multisite: Get bucket location which is located in another zonegroup, will return 301 Moved Permanently ([issue#21125](http://tracker.ceph.com/issues/21125), [pr#17857](https://github.com/ceph/ceph/pull/17857), Shasha Lu)
- rgw: multisite: race between sync of bucket and bucket instance metadata ([issue#21990](http://tracker.ceph.com/issues/21990), [pr#18767](https://github.com/ceph/ceph/pull/18767), Casey Bodley)
- rgw: policy checks missing from Get/SetRequestPayment operations ([issue#21389](http://tracker.ceph.com/issues/21389), [pr#18440](https://github.com/ceph/ceph/pull/18440), Adam C. Emerson)
- rgw: radosgw-admin usage show loops indefinitly ([issue#21196](http://tracker.ceph.com/issues/21196), [pr#18437](https://github.com/ceph/ceph/pull/18437), Mark Kogan)
- rgw: rgw\_file: explicit NFSv3 open() emulation ([issue#21854](http://tracker.ceph.com/issues/21854), [pr#18446](https://github.com/ceph/ceph/pull/18446), Matt Benjamin)
- rgw: rgw\_file: fix write error when the write offset overlaps ([issue#21455](http://tracker.ceph.com/issues/21455), [pr#18004](https://github.com/ceph/ceph/pull/18004), Yao Zongyou)
- rgw: rgw file write error ([issue#21455](http://tracker.ceph.com/issues/21455), [pr#18433](https://github.com/ceph/ceph/pull/18433), Yao Zongyou)
- rgw: s3:GetBucketCORS/s3:PutBucketCORS policy fails with 403 ([issue#21578](http://tracker.ceph.com/issues/21578), [pr#18444](https://github.com/ceph/ceph/pull/18444), Adam C. Emerson)
- rgw: s3:GetBucketLocation bucket policy fails with 403 ([issue#21582](http://tracker.ceph.com/issues/21582), [pr#18443](https://github.com/ceph/ceph/pull/18443), Adam C. Emerson)
- rgw: s3:GetBucketWebsite/PutBucketWebsite fails with 403 ([issue#21597](http://tracker.ceph.com/issues/21597), [pr#18445](https://github.com/ceph/ceph/pull/18445), Adam C. Emerson)
- rgw: setxattrs call leads to different mtimes for bucket index and object ([issue#21200](http://tracker.ceph.com/issues/21200), [pr#17856](https://github.com/ceph/ceph/pull/17856), Abhishek Lekshmanan)
- rgw: stop/join TokenCache revoke thread only if started ([issue#21666](http://tracker.ceph.com/issues/21666), [pr#18138](https://github.com/ceph/ceph/pull/18138), Karol Mroz)
- rgw: string\_view instance points to expired memory in PrefixableSignatureHelper ([issue#21085](http://tracker.ceph.com/issues/21085), [pr#17858](https://github.com/ceph/ceph/pull/17858), Radoslaw Zarzynski)
- rgw: user creation can overwrite existing user even if different uid is given ([issue#21685](http://tracker.ceph.com/issues/21685), [pr#18436](https://github.com/ceph/ceph/pull/18436), Casey Bodley)
- rgw: We cant’t get torrents if objects are encrypted using SSE-C ([issue#21720](http://tracker.ceph.com/issues/21720), [pr#18431](https://github.com/ceph/ceph/pull/18431), Zhang Shaowen)
- rgw: wrong error message is returned when putting container with a name that is too long ([issue#17938](http://tracker.ceph.com/issues/17938), [issue#21169](http://tracker.ceph.com/issues/21169), [issue#17935](http://tracker.ceph.com/issues/17935), [issue#17934](http://tracker.ceph.com/issues/17934), [issue#17936](http://tracker.ceph.com/issues/17936), [pr#17811](https://github.com/ceph/ceph/pull/17811), Radoslaw Zarzynski)
- rgw: zone compression type is not validated ([issue#21775](http://tracker.ceph.com/issues/21775), [pr#18434](https://github.com/ceph/ceph/pull/18434), Casey Bodley)
- tools: ceph-disk create deprecation warnings ([issue#22154](http://tracker.ceph.com/issues/22154), [pr#18989](https://github.com/ceph/ceph/pull/18989), Alfredo Deza)
- tools: ceph-disk: fix ‘–runtime’ omission for ceph-osd service ([issue#21498](http://tracker.ceph.com/issues/21498), [pr#17914](https://github.com/ceph/ceph/pull/17914), Carl Xiong)
- tools: ceph-disk flake8 test fails on very old, and very new, versions of flake8 ([issue#22207](http://tracker.ceph.com/issues/22207), [pr#19152](https://github.com/ceph/ceph/pull/19152), Nathan Cutler)
- tools: ceph-disk: retry on OSError ([issue#21728](http://tracker.ceph.com/issues/21728), [pr#18189](https://github.com/ceph/ceph/pull/18189), Kefu Chai)
- tools: ceph-disk: unlocks dmcrypted partitions when activating them ([issue#20488](http://tracker.ceph.com/issues/20488), [pr#18625](https://github.com/ceph/ceph/pull/18625), Kefu Chai, Felix Winterhalter)
- tools: ceph-kvstore-tool does not call bluestore’s umount when exit ([issue#21625](http://tracker.ceph.com/issues/21625), [pr#18751](https://github.com/ceph/ceph/pull/18751), Chang Liu)
- tools: ceph\_monstore\_tool: rebuild initial mgrmap also ([issue#22266](http://tracker.ceph.com/issues/22266), [pr#19240](https://github.com/ceph/ceph/pull/19240), Kefu Chai)
- tools: ceph-objectstore-tool and ceph-bluestore-tool: backports from master ([issue#21272](http://tracker.ceph.com/issues/21272), [pr#17896](https://github.com/ceph/ceph/pull/17896), Sage Weil, David Zafman)
- tools: ceph\_volume\_client: add get, put, and delete object interfaces ([issue#21601](http://tracker.ceph.com/issues/21601), [pr#18037](https://github.com/ceph/ceph/pull/18037), Ramana Raja)
- tools: cli/crushtools/build.t sometimes fails in jenkins’ make check run ([issue#21758](http://tracker.ceph.com/issues/21758), [pr#18398](https://github.com/ceph/ceph/pull/18398), Kefu Chai, Sage Weil)
