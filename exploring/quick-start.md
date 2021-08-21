I was trying the quick start today

https://cassandra.apache.org/_/quickstart.html

I tried this

```bash
$ docker pull cassandra:latest
$ docker run --name cassandra cassandra
```

But later I realized no ports are exposed etc

So started using the other command

```bash
~ $ docker run --rm -d --name cassandra --hostname cassandra --network cassandra cassandra
7d0e3def9d06347159cb8cccd501fc2b8e467e20a2f4336c3080f850dd5ae6d2
docker: Error response from daemon: network cassandra not found.

~ $ docker network

Usage:  docker network COMMAND

Manage networks

Commands:
  connect     Connect a container to a network
  create      Create a network
  disconnect  Disconnect a container from a network
  inspect     Display detailed information on one or more networks
  ls          List networks
  prune       Remove all unused networks
  rm          Remove one or more networks

Run 'docker network COMMAND --help' for more information on a command.

~ $ docker network create cassandra
df8b9bc775957ec1e1197dbe79bad189a127eba83de5589f15ff01c96e82c7f0

~ $ docker run --rm -d --name cassandra --hostname cassandra --network cassandra cassandra
9fc149b8dd0ba7b88cf4283ef86d760ea46c2182d3050c3eb03c8c400d41d854

~ $ docker ps
CONTAINER ID   IMAGE       COMMAND                  CREATED         STATUS         PORTS                                         NAMES
9fc149b8dd0b   cassandra   "docker-entrypoint.s…"   8 seconds ago   Up 7 seconds   7000-7001/tcp, 7199/tcp, 9042/tcp, 9160/tcp   cassandra

~ $ docker logs cassandra
OpenJDK 64-Bit Server VM warning: Option UseConcMarkSweepGC was deprecated in version 9.0 and will likely be removed in a future release.
CompileCommand: dontinline org/apache/cassandra/db/Columns$Serializer.deserializeLargeSubset(Lorg/apache/cassandra/io/util/DataInputPlus;Lorg/apache/cassandra/db/Columns;I)Lorg/apache/cassandra/db/Columns;
CompileCommand: dontinline org/apache/cassandra/db/Columns$Serializer.serializeLargeSubset(Ljava/util/Collection;ILorg/apache/cassandra/db/Columns;ILorg/apache/cassandra/io/util/DataOutputPlus;)V
CompileCommand: dontinline org/apache/cassandra/db/Columns$Serializer.serializeLargeSubsetSize(Ljava/util/Collection;ILorg/apache/cassandra/db/Columns;I)I
CompileCommand: dontinline org/apache/cassandra/db/commitlog/AbstractCommitLogSegmentManager.advanceAllocatingFrom(Lorg/apache/cassandra/db/commitlog/CommitLogSegment;)V
CompileCommand: dontinline org/apache/cassandra/db/transform/BaseIterator.tryGetMoreContents()Z
CompileCommand: dontinline org/apache/cassandra/db/transform/StoppingTransformation.stop()V
CompileCommand: dontinline org/apache/cassandra/db/transform/StoppingTransformation.stopInPartition()V
CompileCommand: dontinline org/apache/cassandra/io/util/BufferedDataOutputStreamPlus.doFlush(I)V
CompileCommand: dontinline org/apache/cassandra/io/util/BufferedDataOutputStreamPlus.writeSlow(JI)V
CompileCommand: dontinline org/apache/cassandra/io/util/RebufferingInputStream.readPrimitiveSlowly(I)J
CompileCommand: exclude org/apache/cassandra/utils/JVMStabilityInspector.forceHeapSpaceOomMaybe(Ljava/lang/OutOfMemoryError;)V
CompileCommand: inline org/apache/cassandra/db/rows/UnfilteredSerializer.serializeRowBody(Lorg/apache/cassandra/db/rows/Row;ILorg/apache/cassandra/db/rows/SerializationHelper;Lorg/apache/cassandra/io/util/DataOutputPlus;)V
CompileCommand: inline org/apache/cassandra/io/util/Memory.checkBounds(JJ)V
CompileCommand: inline org/apache/cassandra/io/util/SafeMemory.checkBounds(JJ)V
CompileCommand: inline org/apache/cassandra/net/FrameDecoderWith8bHeader.decode(Ljava/util/Collection;Lorg/apache/cassandra/net/ShareableBytes;I)V
CompileCommand: inline org/apache/cassandra/service/reads/repair/RowIteratorMergeListener.applyToPartition(ILjava/util/function/Consumer;)V
CompileCommand: inline org/apache/cassandra/utils/AsymmetricOrdering.selectBoundary(Lorg/apache/cassandra/utils/AsymmetricOrdering/Op;II)I
CompileCommand: inline org/apache/cassandra/utils/AsymmetricOrdering.strictnessOfLessThan(Lorg/apache/cassandra/utils/AsymmetricOrdering/Op;)I
CompileCommand: inline org/apache/cassandra/utils/BloomFilter.indexes(Lorg/apache/cassandra/utils/IFilter/FilterKey;)[J
CompileCommand: inline org/apache/cassandra/utils/BloomFilter.setIndexes(JJIJ[J)V
CompileCommand: inline org/apache/cassandra/utils/ByteBufferUtil.compare(Ljava/nio/ByteBuffer;[B)I
CompileCommand: inline org/apache/cassandra/utils/ByteBufferUtil.compare([BLjava/nio/ByteBuffer;)I
CompileCommand: inline org/apache/cassandra/utils/ByteBufferUtil.compareUnsigned(Ljava/nio/ByteBuffer;Ljava/nio/ByteBuffer;)I
CompileCommand: inline org/apache/cassandra/utils/FastByteOperations$UnsafeOperations.compareTo(Ljava/lang/Object;JILjava/lang/Object;JI)I
CompileCommand: inline org/apache/cassandra/utils/FastByteOperations$UnsafeOperations.compareTo(Ljava/lang/Object;JILjava/nio/ByteBuffer;)I
CompileCommand: inline org/apache/cassandra/utils/FastByteOperations$UnsafeOperations.compareTo(Ljava/nio/ByteBuffer;Ljava/nio/ByteBuffer;)I
CompileCommand: inline org/apache/cassandra/utils/memory/BufferPool$LocalPool.tryGetInternal(IZ)Ljava/nio/ByteBuffer;
CompileCommand: inline org/apache/cassandra/utils/vint/VIntCoding.encodeUnsignedVInt(JI)[B
CompileCommand: inline org/apache/cassandra/utils/vint/VIntCoding.encodeUnsignedVInt(JI[B)V
CompileCommand: inline org/apache/cassandra/utils/vint/VIntCoding.writeUnsignedVInt(JLjava/io/DataOutput;)V
CompileCommand: inline org/apache/cassandra/utils/vint/VIntCoding.writeUnsignedVInt(JLjava/nio/ByteBuffer;)V
CompileCommand: inline org/apache/cassandra/utils/vint/VIntCoding.writeVInt(JLjava/io/DataOutput;)V
INFO  [main] 2021-08-21 06:47:20,353 YamlConfigurationLoader.java:93 - Configuration location: file:/etc/cassandra/cassandra.yaml
INFO  [main] 2021-08-21 06:47:20,788 Config.java:691 - Node configuration:[allocate_tokens_for_keyspace=null; allocate_tokens_for_local_replication_factor=3; audit_logging_options=AuditLogOptions{enabled=false, logger='BinAuditLogger', included_keyspaces='', excluded_keyspaces='system,system_schema,system_virtual_schema', included_categories='', excluded_categories='', included_users='', excluded_users='', audit_logs_dir='/opt/cassandra/logs/audit/', archive_command='', roll_cycle='HOURLY', block=true, max_queue_weight=268435456, max_log_size=17179869184}; authenticator=AllowAllAuthenticator; authorizer=AllowAllAuthorizer; auto_bootstrap=true; auto_optimise_full_repair_streams=false; auto_optimise_inc_repair_streams=false; auto_optimise_preview_repair_streams=false; auto_snapshot=true; autocompaction_on_startup_enabled=true; automatic_sstable_upgrade=false; back_pressure_enabled=false; back_pressure_strategy=null; batch_size_fail_threshold_in_kb=50; batch_size_warn_threshold_in_kb=5; batchlog_replay_throttle_in_kb=1024; block_for_peers_in_remote_dcs=false; block_for_peers_timeout_in_secs=10; broadcast_address=172.19.0.2; broadcast_rpc_address=172.19.0.2; buffer_pool_use_heap_if_exhausted=false; cas_contention_timeout_in_ms=1000; cdc_enabled=false; cdc_free_space_check_interval_ms=250; cdc_raw_directory=null; cdc_total_space_in_mb=0; check_for_duplicate_rows_during_compaction=true; check_for_duplicate_rows_during_reads=true; client_encryption_options=<REDACTED>; cluster_name=Test Cluster; column_index_cache_size_in_kb=2; column_index_size_in_kb=64; commit_failure_policy=stop; commitlog_compression=null; commitlog_directory=null; commitlog_max_compression_buffers_in_pool=3; commitlog_periodic_queue_size=-1; commitlog_segment_size_in_mb=32; commitlog_sync=periodic; commitlog_sync_batch_window_in_ms=NaN; commitlog_sync_group_window_in_ms=NaN; commitlog_sync_period_in_ms=10000; commitlog_total_space_in_mb=null; compaction_large_partition_warning_threshold_mb=100; compaction_throughput_mb_per_sec=64; concurrent_compactors=null; concurrent_counter_writes=32; concurrent_materialized_view_builders=1; concurrent_materialized_view_writes=32; concurrent_reads=32; concurrent_replicates=null; concurrent_validations=0; concurrent_writes=32; consecutive_message_errors_threshold=1; corrupted_tombstone_strategy=disabled; counter_cache_keys_to_save=2147483647; counter_cache_save_period=7200; counter_cache_size_in_mb=null; counter_write_request_timeout_in_ms=5000; credentials_cache_max_entries=1000; credentials_update_interval_in_ms=-1; credentials_validity_in_ms=2000; cross_node_timeout=true; data_file_directories=[Ljava.lang.String;@42257bdd; diagnostic_events_enabled=false; disk_access_mode=auto; disk_failure_policy=stop; disk_optimization_estimate_percentile=0.95; disk_optimization_page_cross_chance=0.1; disk_optimization_strategy=ssd; dynamic_snitch=true; dynamic_snitch_badness_threshold=1.0; dynamic_snitch_reset_interval_in_ms=600000; dynamic_snitch_update_interval_in_ms=100; enable_drop_compact_storage=false; enable_materialized_views=false; enable_sasi_indexes=false; enable_scripted_user_defined_functions=false; enable_transient_replication=false; enable_user_defined_functions=false; enable_user_defined_functions_threads=true; endpoint_snitch=SimpleSnitch; file_cache_enabled=false; file_cache_round_up=null; file_cache_size_in_mb=null; flush_compression=fast; full_query_logging_options=FullQueryLoggerOptions{log_dir='', archive_command='', roll_cycle='HOURLY', block=true, max_queue_weight=268435456, max_log_size=17179869184}; gc_log_threshold_in_ms=200; gc_warn_threshold_in_ms=1000; hinted_handoff_disabled_datacenters=[]; hinted_handoff_enabled=true; hinted_handoff_throttle_in_kb=1024; hints_compression=null; hints_directory=null; hints_flush_period_in_ms=10000; ideal_consistency_level=null; incremental_backups=false; index_summary_capacity_in_mb=null; index_summary_resize_interval_in_minutes=60; initial_range_tombstone_list_allocation_size=1; initial_token=null; inter_dc_stream_throughput_outbound_megabits_per_sec=200; inter_dc_tcp_nodelay=false; internode_application_receive_queue_capacity_in_bytes=4194304; internode_application_receive_queue_reserve_endpoint_capacity_in_bytes=134217728; internode_application_receive_queue_reserve_global_capacity_in_bytes=536870912; internode_application_send_queue_capacity_in_bytes=4194304; internode_application_send_queue_reserve_endpoint_capacity_in_bytes=134217728; internode_application_send_queue_reserve_global_capacity_in_bytes=536870912; internode_authenticator=null; internode_compression=dc; internode_max_message_size_in_bytes=null; internode_socket_receive_buffer_size_in_bytes=0; internode_socket_send_buffer_size_in_bytes=0; internode_streaming_tcp_user_timeout_in_ms=300000; internode_tcp_connect_timeout_in_ms=2000; internode_tcp_user_timeout_in_ms=30000; key_cache_keys_to_save=2147483647; key_cache_migrate_during_compaction=true; key_cache_save_period=14400; key_cache_size_in_mb=null; keyspace_count_warn_threshold=40; listen_address=172.19.0.2; listen_interface=null; listen_interface_prefer_ipv6=false; listen_on_broadcast_address=false; local_system_data_file_directory=null; max_concurrent_automatic_sstable_upgrades=1; max_hint_window_in_ms=10800000; max_hints_delivery_threads=2; max_hints_file_size_in_mb=128; max_mutation_size_in_kb=null; max_streaming_retries=3; max_value_size_in_mb=256; memtable_allocation_type=heap_buffers; memtable_cleanup_threshold=null; memtable_flush_writers=0; memtable_heap_space_in_mb=null; memtable_offheap_space_in_mb=null; min_free_space_per_drive_in_mb=50; native_transport_allow_older_protocols=true; native_transport_flush_in_batches_legacy=false; native_transport_idle_timeout_in_ms=0; native_transport_max_concurrent_connections=-1; native_transport_max_concurrent_connections_per_ip=-1; native_transport_max_concurrent_requests_in_bytes=-1; native_transport_max_concurrent_requests_in_bytes_per_ip=-1; native_transport_max_frame_size_in_mb=256; native_transport_max_negotiable_protocol_version=null; native_transport_max_threads=128; native_transport_port=9042; native_transport_port_ssl=null; native_transport_receive_queue_capacity_in_bytes=1048576; network_authorizer=AllowAllNetworkAuthorizer; networking_cache_size_in_mb=null; num_tokens=16; otc_coalescing_enough_coalesced_messages=8; otc_coalescing_strategy=DISABLED; otc_coalescing_window_us=200; partitioner=org.apache.cassandra.dht.Murmur3Partitioner; periodic_commitlog_sync_lag_block_in_ms=null; permissions_cache_max_entries=1000; permissions_update_interval_in_ms=-1; permissions_validity_in_ms=2000; phi_convict_threshold=8.0; prepared_statements_cache_size_mb=null; range_request_timeout_in_ms=10000; range_tombstone_list_growth_factor=1.5; read_request_timeout_in_ms=5000; reject_repair_compaction_threshold=2147483647; repair_command_pool_full_strategy=queue; repair_command_pool_size=0; repair_session_max_tree_depth=null; repair_session_space_in_mb=null; repaired_data_tracking_for_partition_reads_enabled=false; repaired_data_tracking_for_range_reads_enabled=false; report_unconfirmed_repaired_data_mismatches=false; request_timeout_in_ms=10000; role_manager=CassandraRoleManager; roles_cache_max_entries=1000; roles_update_interval_in_ms=-1; roles_validity_in_ms=2000; row_cache_class_name=org.apache.cassandra.cache.OHCProvider; row_cache_keys_to_save=2147483647; row_cache_save_period=0; row_cache_size_in_mb=0; rpc_address=0.0.0.0; rpc_interface=null; rpc_interface_prefer_ipv6=false; rpc_keepalive=true; saved_caches_directory=null; seed_provider=org.apache.cassandra.locator.SimpleSeedProvider{seeds=172.19.0.2}; server_encryption_options=<REDACTED>; slow_query_log_timeout_in_ms=500; snapshot_before_compaction=false; snapshot_links_per_second=0; snapshot_on_duplicate_row_detection=false; snapshot_on_repaired_data_mismatch=false; ssl_storage_port=7001; sstable_preemptive_open_interval_in_mb=50; start_native_transport=true; storage_port=7000; stream_entire_sstables=true; stream_throughput_outbound_megabits_per_sec=200; streaming_connections_per_host=1; streaming_keep_alive_period_in_secs=300; table_count_warn_threshold=150; tombstone_failure_threshold=100000; tombstone_warn_threshold=1000; tracetype_query_ttl=86400; tracetype_repair_ttl=604800; transparent_data_encryption_options=org.apache.cassandra.config.TransparentDataEncryptionOptions@7689ddef; trickle_fsync=false; trickle_fsync_interval_in_kb=10240; truncate_request_timeout_in_ms=60000; unlogged_batch_across_partitions_warn_threshold=10; use_offheap_merkle_trees=true; user_defined_function_fail_timeout=1500; user_defined_function_warn_timeout=500; user_function_timeout_policy=die; validation_preview_purge_head_start_in_sec=3600; windows_timer_interval=1; write_request_timeout_in_ms=2000]
INFO  [main] 2021-08-21 06:47:20,791 DatabaseDescriptor.java:416 - DiskAccessMode 'auto' determined to be mmap, indexAccessMode is mmap
INFO  [main] 2021-08-21 06:47:20,792 DatabaseDescriptor.java:477 - Global memtable on-heap threshold is enabled at 606MB
INFO  [main] 2021-08-21 06:47:20,792 DatabaseDescriptor.java:481 - Global memtable off-heap threshold is enabled at 606MB
INFO  [main] 2021-08-21 06:47:20,906 JMXServerUtils.java:271 - Configured JMX server at: service:jmx:rmi://127.0.0.1/jndi/rmi://127.0.0.1:7199/jmxrmi
INFO  [main] 2021-08-21 06:47:20,911 CassandraDaemon.java:623 - Hostname: cassandra:7000:7001
INFO  [main] 2021-08-21 06:47:20,912 CassandraDaemon.java:630 - JVM vendor/version: OpenJDK 64-Bit Server VM/11.0.11
INFO  [main] 2021-08-21 06:47:20,913 CassandraDaemon.java:631 - Heap size: 2.371GiB/2.371GiB
INFO  [main] 2021-08-21 06:47:20,914 CassandraDaemon.java:636 - CodeHeap 'non-nmethods' Non-heap memory: init = 2555904(2496K) used = 1192832(1164K) committed = 2555904(2496K) max = 5836800(5700K)
INFO  [main] 2021-08-21 06:47:20,924 CassandraDaemon.java:636 - Metaspace Non-heap memory: init = 0(0K) used = 26309840(25693K) committed = 26906624(26276K) max = -1(-1K)
INFO  [main] 2021-08-21 06:47:20,924 CassandraDaemon.java:636 - CodeHeap 'profiled nmethods' Non-heap memory: init = 2555904(2496K) used = 3936256(3844K) committed = 3997696(3904K) max = 122908672(120028K)
INFO  [main] 2021-08-21 06:47:20,925 CassandraDaemon.java:636 - Compressed Class Space Non-heap memory: init = 0(0K) used = 3030440(2959K) committed = 3297280(3220K) max = 1073741824(1048576K)
INFO  [main] 2021-08-21 06:47:20,925 CassandraDaemon.java:636 - Par Eden Space Heap memory: init = 521797632(509568K) used = 146133560(142708K) committed = 521797632(509568K) max = 521797632(509568K)
INFO  [main] 2021-08-21 06:47:20,926 CassandraDaemon.java:636 - Par Survivor Space Heap memory: init = 65208320(63680K) used = 0(0K) committed = 65208320(63680K) max = 65208320(63680K)
INFO  [main] 2021-08-21 06:47:20,926 CassandraDaemon.java:636 - CodeHeap 'non-profiled nmethods' Non-heap memory: init = 2555904(2496K) used = 719744(702K) committed = 2555904(2496K) max = 122912768(120032K)
INFO  [main] 2021-08-21 06:47:20,927 CassandraDaemon.java:636 - CMS Old Gen Heap memory: init = 1958739968(1912832K) used = 0(0K) committed = 1958739968(1912832K) max = 1958739968(1912832K)
INFO  [main] 2021-08-21 06:47:20,927 CassandraDaemon.java:638 - Classpath: /etc/cassandra:/opt/cassandra/lib/HdrHistogram-2.1.9.jar:/opt/cassandra/lib/ST4-4.0.8.jar:/opt/cassandra/lib/airline-0.8.jar:/opt/cassandra/lib/antlr-runtime-3.5.2.jar:/opt/cassandra/lib/apache-cassandra-4.0.0.jar:/opt/cassandra/lib/asm-7.1.jar:/opt/cassandra/lib/caffeine-2.3.5.jar:/opt/cassandra/lib/cassandra-driver-core-3.11.0-shaded.jar:/opt/cassandra/lib/chronicle-bytes-2.20.111.jar:/opt/cassandra/lib/chronicle-core-2.20.126.jar:/opt/cassandra/lib/chronicle-queue-5.20.123.jar:/opt/cassandra/lib/chronicle-threads-2.20.111.jar:/opt/cassandra/lib/chronicle-wire-2.20.117.jar:/opt/cassandra/lib/commons-cli-1.1.jar:/opt/cassandra/lib/commons-codec-1.9.jar:/opt/cassandra/lib/commons-lang3-3.11.jar:/opt/cassandra/lib/commons-math3-3.2.jar:/opt/cassandra/lib/concurrent-trees-2.4.0.jar:/opt/cassandra/lib/ecj-4.6.1.jar:/opt/cassandra/lib/guava-27.0-jre.jar:/opt/cassandra/lib/high-scale-lib-1.0.6.jar:/opt/cassandra/lib/hppc-0.8.1.jar:/opt/cassandra/lib/j2objc-annotations-1.3.jar:/opt/cassandra/lib/jackson-annotations-2.9.10.jar:/opt/cassandra/lib/jackson-core-2.9.10.jar:/opt/cassandra/lib/jackson-databind-2.9.10.8.jar:/opt/cassandra/lib/jamm-0.3.2.jar:/opt/cassandra/lib/java-cup-runtime-11b-20160615.jar:/opt/cassandra/lib/javax.inject-1.jar:/opt/cassandra/lib/jbcrypt-0.3m.jar:/opt/cassandra/lib/jcl-over-slf4j-1.7.25.jar:/opt/cassandra/lib/jcommander-1.30.jar:/opt/cassandra/lib/jctools-core-3.1.0.jar:/opt/cassandra/lib/jflex-1.8.2.jar:/opt/cassandra/lib/jna-5.6.0.jar:/opt/cassandra/lib/json-simple-1.1.jar:/opt/cassandra/lib/jvm-attach-api-1.5.jar:/opt/cassandra/lib/log4j-over-slf4j-1.7.25.jar:/opt/cassandra/lib/logback-classic-1.2.3.jar:/opt/cassandra/lib/logback-core-1.2.3.jar:/opt/cassandra/lib/lz4-java-1.7.1.jar:/opt/cassandra/lib/metrics-core-3.1.5.jar:/opt/cassandra/lib/metrics-jvm-3.1.5.jar:/opt/cassandra/lib/metrics-logback-3.1.5.jar:/opt/cassandra/lib/mxdump-0.14.jar:/opt/cassandra/lib/netty-all-4.1.58.Final.jar:/opt/cassandra/lib/netty-tcnative-boringssl-static-2.0.36.Final.jar:/opt/cassandra/lib/ohc-core-0.5.1.jar:/opt/cassandra/lib/ohc-core-j8-0.5.1.jar:/opt/cassandra/lib/psjava-0.1.19.jar:/opt/cassandra/lib/reporter-config-base-3.0.3.jar:/opt/cassandra/lib/reporter-config3-3.0.3.jar:/opt/cassandra/lib/sigar-1.6.4.jar:/opt/cassandra/lib/sjk-cli-0.14.jar:/opt/cassandra/lib/sjk-core-0.14.jar:/opt/cassandra/lib/sjk-json-0.14.jar:/opt/cassandra/lib/sjk-stacktrace-0.14.jar:/opt/cassandra/lib/slf4j-api-1.7.25.jar:/opt/cassandra/lib/snakeyaml-1.26.jar:/opt/cassandra/lib/snappy-java-1.1.2.6.jar:/opt/cassandra/lib/snowball-stemmer-1.3.0.581.1.jar:/opt/cassandra/lib/stream-2.5.2.jar:/opt/cassandra/lib/zstd-jni-1.3.8-5.jar:/opt/cassandra/lib/jsr223/*/*.jar:
INFO  [main] 2021-08-21 06:47:20,928 CassandraDaemon.java:640 - JVM Arguments: [-ea, -da:net.openhft..., -XX:+UseThreadPriorities, -XX:+HeapDumpOnOutOfMemoryError, -Xss256k, -XX:+AlwaysPreTouch, -XX:-UseBiasedLocking, -XX:+UseTLAB, -XX:+ResizeTLAB, -XX:+UseNUMA, -XX:+PerfDisableSharedMem, -Djava.net.preferIPv4Stack=true, -XX:+UseConcMarkSweepGC, -XX:+CMSParallelRemarkEnabled, -XX:SurvivorRatio=8, -XX:MaxTenuringThreshold=1, -XX:CMSInitiatingOccupancyFraction=75, -XX:+UseCMSInitiatingOccupancyOnly, -XX:CMSWaitDuration=10000, -XX:+CMSParallelInitialMarkEnabled, -XX:+CMSEdenChunksRecordAlways, -XX:+CMSClassUnloadingEnabled, -Djdk.attach.allowAttachSelf=true, --add-exports=java.base/jdk.internal.misc=ALL-UNNAMED, --add-exports=java.base/jdk.internal.ref=ALL-UNNAMED, --add-exports=java.base/sun.nio.ch=ALL-UNNAMED, --add-exports=java.management.rmi/com.sun.jmx.remote.internal.rmi=ALL-UNNAMED, --add-exports=java.rmi/sun.rmi.registry=ALL-UNNAMED, --add-exports=java.rmi/sun.rmi.server=ALL-UNNAMED, --add-exports=java.sql/java.sql=ALL-UNNAMED, --add-opens=java.base/java.lang.module=ALL-UNNAMED, --add-opens=java.base/jdk.internal.loader=ALL-UNNAMED, --add-opens=java.base/jdk.internal.ref=ALL-UNNAMED, --add-opens=java.base/jdk.internal.reflect=ALL-UNNAMED, --add-opens=java.base/jdk.internal.math=ALL-UNNAMED, --add-opens=java.base/jdk.internal.module=ALL-UNNAMED, --add-opens=java.base/jdk.internal.util.jar=ALL-UNNAMED, --add-opens=jdk.management/com.sun.management.internal=ALL-UNNAMED, -Dio.netty.tryReflectionSetAccessible=true, -Xlog:gc=info,heap*=trace,age*=debug,safepoint=info,promotion*=trace:file=/opt/cassandra/logs/gc.log:time,uptime,pid,tid,level:filecount=10,filesize=10485760, -Xms2490M, -Xmx2490M, -Xmn622M, -XX:+UseCondCardMark, -XX:CompileCommandFile=/etc/cassandra/hotspot_compiler, -javaagent:/opt/cassandra/lib/jamm-0.3.2.jar, -Dcassandra.jmx.local.port=7199, -Dcom.sun.management.jmxremote.authenticate=false, -Dcom.sun.management.jmxremote.password.file=/etc/cassandra/jmxremote.password, -Djava.library.path=/opt/cassandra/lib/sigar-bin, -Dcassandra.libjemalloc=/usr/local/lib/libjemalloc.so, -XX:OnOutOfMemoryError=kill -9 %p, -Dlogback.configurationFile=logback.xml, -Dcassandra.logdir=/opt/cassandra/logs, -Dcassandra.storagedir=/opt/cassandra/data, -Dcassandra-foreground=yes]
WARN  [main] 2021-08-21 06:47:20,988 NativeLibrary.java:201 - Unable to lock JVM memory (ENOMEM). This can result in part of the JVM being swapped out, especially with mmapped I/O enabled. Increase RLIMIT_MEMLOCK.
INFO  [main] 2021-08-21 06:47:21,035 MonotonicClock.java:199 - Scheduling approximate time conversion task with an interval of 10000 milliseconds
INFO  [main] 2021-08-21 06:47:21,038 MonotonicClock.java:335 - Scheduling approximate time-check task with a precision of 2 milliseconds
INFO  [main] 2021-08-21 06:47:21,040 StartupChecks.java:147 - jemalloc seems to be preloaded from /usr/local/lib/libjemalloc.so
WARN  [main] 2021-08-21 06:47:21,041 StartupChecks.java:187 - JMX is not enabled to receive remote connections. Please see cassandra-env.sh for more info.
INFO  [main] 2021-08-21 06:47:21,042 SigarLibrary.java:44 - Initializing SIGAR library
WARN  [main] 2021-08-21 06:47:21,051 SigarLibrary.java:174 - Cassandra server running in degraded mode. Is swap disabled? : false,  Address space adequate? : true,  nofile limit adequate? : true, nproc limit adequate? : true 
WARN  [main] 2021-08-21 06:47:21,052 StartupChecks.java:329 - Maximum number of memory map areas per process (vm.max_map_count) 262144 is too low, recommended value: 1048575, you can change it with sysctl.
INFO  [main] 2021-08-21 06:47:21,441 Keyspace.java:386 - Creating replication strategy system params KeyspaceParams{durable_writes=true, replication=ReplicationParams{class=org.apache.cassandra.locator.LocalStrategy}}
INFO  [main] 2021-08-21 06:47:21,482 ColumnFamilyStore.java:385 - Initializing system.IndexInfo
INFO  [main] 2021-08-21 06:47:22,012 ColumnFamilyStore.java:385 - Initializing system.batches
INFO  [main] 2021-08-21 06:47:22,024 ColumnFamilyStore.java:385 - Initializing system.paxos
INFO  [main] 2021-08-21 06:47:22,040 ColumnFamilyStore.java:385 - Initializing system.local
INFO  [main] 2021-08-21 06:47:22,048 ColumnFamilyStore.java:385 - Initializing system.peers_v2
INFO  [main] 2021-08-21 06:47:22,060 ColumnFamilyStore.java:385 - Initializing system.peers
INFO  [main] 2021-08-21 06:47:22,069 ColumnFamilyStore.java:385 - Initializing system.peer_events_v2
INFO  [main] 2021-08-21 06:47:22,079 ColumnFamilyStore.java:385 - Initializing system.peer_events
INFO  [main] 2021-08-21 06:47:22,088 ColumnFamilyStore.java:385 - Initializing system.compaction_history
INFO  [main] 2021-08-21 06:47:22,097 ColumnFamilyStore.java:385 - Initializing system.sstable_activity
INFO  [main] 2021-08-21 06:47:22,106 ColumnFamilyStore.java:385 - Initializing system.size_estimates
INFO  [main] 2021-08-21 06:47:22,115 ColumnFamilyStore.java:385 - Initializing system.table_estimates
INFO  [main] 2021-08-21 06:47:22,124 ColumnFamilyStore.java:385 - Initializing system.available_ranges_v2
INFO  [main] 2021-08-21 06:47:22,133 ColumnFamilyStore.java:385 - Initializing system.available_ranges
INFO  [main] 2021-08-21 06:47:22,142 ColumnFamilyStore.java:385 - Initializing system.transferred_ranges_v2
INFO  [main] 2021-08-21 06:47:22,151 ColumnFamilyStore.java:385 - Initializing system.transferred_ranges
INFO  [main] 2021-08-21 06:47:22,160 ColumnFamilyStore.java:385 - Initializing system.view_builds_in_progress
INFO  [main] 2021-08-21 06:47:22,169 ColumnFamilyStore.java:385 - Initializing system.built_views
INFO  [main] 2021-08-21 06:47:22,177 ColumnFamilyStore.java:385 - Initializing system.prepared_statements
INFO  [main] 2021-08-21 06:47:22,186 ColumnFamilyStore.java:385 - Initializing system.repairs
INFO  [main] 2021-08-21 06:47:22,391 QueryProcessor.java:106 - Initialized prepared statement caches with 10 MB
INFO  [main] 2021-08-21 06:47:22,518 Keyspace.java:386 - Creating replication strategy system_schema params KeyspaceParams{durable_writes=true, replication=ReplicationParams{class=org.apache.cassandra.locator.LocalStrategy}}
INFO  [main] 2021-08-21 06:47:22,522 ColumnFamilyStore.java:385 - Initializing system_schema.keyspaces
INFO  [main] 2021-08-21 06:47:22,530 ColumnFamilyStore.java:385 - Initializing system_schema.tables
INFO  [main] 2021-08-21 06:47:22,538 ColumnFamilyStore.java:385 - Initializing system_schema.columns
INFO  [main] 2021-08-21 06:47:22,547 ColumnFamilyStore.java:385 - Initializing system_schema.triggers
INFO  [main] 2021-08-21 06:47:22,554 ColumnFamilyStore.java:385 - Initializing system_schema.dropped_columns
INFO  [main] 2021-08-21 06:47:22,562 ColumnFamilyStore.java:385 - Initializing system_schema.views
INFO  [main] 2021-08-21 06:47:22,570 ColumnFamilyStore.java:385 - Initializing system_schema.types
INFO  [main] 2021-08-21 06:47:22,578 ColumnFamilyStore.java:385 - Initializing system_schema.functions
INFO  [main] 2021-08-21 06:47:22,585 ColumnFamilyStore.java:385 - Initializing system_schema.aggregates
INFO  [main] 2021-08-21 06:47:22,593 ColumnFamilyStore.java:385 - Initializing system_schema.indexes
INFO  [main] 2021-08-21 06:47:22,668 SystemKeyspaceMigrator40.java:76 - system.peers_v2 table was empty, migrating legacy system.peers, if this fails you should fix the issue and then truncate system.peers_v2 to have it try again.
INFO  [main] 2021-08-21 06:47:22,675 SystemKeyspaceMigrator40.java:100 - Migrating rows from legacy system.peers to system.peers_v2
INFO  [main] 2021-08-21 06:47:22,680 SystemKeyspaceMigrator40.java:119 - Migrated 0 rows from legacy system.peers to system.peers_v2
INFO  [main] 2021-08-21 06:47:22,680 SystemKeyspaceMigrator40.java:129 - system.peer_events_v2 table was empty, migrating legacy system.peer_events to system.peer_events_v2
INFO  [main] 2021-08-21 06:47:22,681 SystemKeyspaceMigrator40.java:152 - Migrated 0 rows from legacy system.peer_events to system.peer_events_v2
INFO  [main] 2021-08-21 06:47:22,682 SystemKeyspaceMigrator40.java:162 - system.transferred_ranges_v2 table was empty, migrating legacy system.transferred_ranges to system.transferred_ranges_v2
INFO  [main] 2021-08-21 06:47:22,684 SystemKeyspaceMigrator40.java:190 - Migrated 0 rows from legacy system.transferred_ranges to system.transferred_ranges_v2
INFO  [main] 2021-08-21 06:47:22,684 SystemKeyspaceMigrator40.java:200 - system.available_ranges_v2 table was empty, migrating legacy system.available_ranges to system.available_ranges_v2
INFO  [main] 2021-08-21 06:47:22,685 SystemKeyspaceMigrator40.java:226 - Migrated 0 rows from legacy system.available_ranges to system.available_ranges_v2
INFO  [main] 2021-08-21 06:47:22,685 StorageService.java:836 - Populating token metadata from system tables
INFO  [main] 2021-08-21 06:47:22,709 StorageService.java:830 - Token metadata: 
INFO  [main] 2021-08-21 06:47:22,749 CacheService.java:100 - Initializing key cache with capacity of 100 MBs.
INFO  [main] 2021-08-21 06:47:22,762 CacheService.java:122 - Initializing row cache with capacity of 0 MBs
INFO  [main] 2021-08-21 06:47:22,764 CacheService.java:151 - Initializing counter cache with capacity of 50 MBs
INFO  [main] 2021-08-21 06:47:22,766 CacheService.java:162 - Scheduling counter cache save to every 7200 seconds (going to save all keys).
INFO  [main] 2021-08-21 06:47:22,792 CommitLog.java:168 - No commitlog files found; skipping replay
INFO  [main] 2021-08-21 06:47:22,792 StorageService.java:836 - Populating token metadata from system tables
INFO  [main] 2021-08-21 06:47:22,804 StorageService.java:830 - Token metadata: 
INFO  [main] 2021-08-21 06:47:22,922 ColumnFamilyStore.java:2242 - Truncating system.size_estimates
INFO  [main] 2021-08-21 06:47:22,946 ColumnFamilyStore.java:2279 - Truncating system.size_estimates with truncatedAt=1629528442928
INFO  [main] 2021-08-21 06:47:22,980 ColumnFamilyStore.java:878 - Enqueuing flush of local: 2.199KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:47:23,041 Memtable.java:469 - Writing Memtable-local@995377569(0.429KiB serialized bytes, 3 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:47:23,044 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-1-big-Data.db (0.224KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=31191)
INFO  [MemtableFlushWriter:1] 2021-08-21 06:47:23,087 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb_txn_flush_a3759e80-024b-11ec-8163-d1ebb543407f.log 
INFO  [main] 2021-08-21 06:47:23,098 ColumnFamilyStore.java:2306 - Truncate of system.size_estimates is complete
INFO  [main] 2021-08-21 06:47:23,098 ColumnFamilyStore.java:2242 - Truncating system.table_estimates
INFO  [main] 2021-08-21 06:47:23,099 ColumnFamilyStore.java:2279 - Truncating system.table_estimates with truncatedAt=1629528443099
INFO  [main] 2021-08-21 06:47:23,102 ColumnFamilyStore.java:878 - Enqueuing flush of local: 0.576KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:47:23,107 Memtable.java:469 - Writing Memtable-local@1210431984(0.091KiB serialized bytes, 1 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:47:23,108 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-2-big-Data.db (0.063KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=31302)
INFO  [MemtableFlushWriter:2] 2021-08-21 06:47:23,118 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb_txn_flush_a3879fe0-024b-11ec-8163-d1ebb543407f.log 
INFO  [main] 2021-08-21 06:47:23,120 ColumnFamilyStore.java:2306 - Truncate of system.table_estimates is complete
INFO  [main] 2021-08-21 06:47:23,124 QueryProcessor.java:150 - Preloaded 0 prepared statements
INFO  [main] 2021-08-21 06:47:23,124 StorageService.java:734 - Cassandra version: 4.0.0
INFO  [main] 2021-08-21 06:47:23,124 StorageService.java:735 - CQL version: 3.4.5
INFO  [main] 2021-08-21 06:47:23,125 StorageService.java:736 - Native protocol supported versions: 3/v3, 4/v4, 5/v5, 6/v6-beta (default: 5/v5)
INFO  [main] 2021-08-21 06:47:23,161 IndexSummaryManager.java:87 - Initializing index summary manager with a memory pool size of 121 MB and a resize interval of 60 minutes
INFO  [main] 2021-08-21 06:47:23,163 StorageService.java:753 - Loading persisted ring state
INFO  [main] 2021-08-21 06:47:23,163 StorageService.java:836 - Populating token metadata from system tables
INFO  [main] 2021-08-21 06:47:23,192 BufferPools.java:49 - Global buffer pool limit is 512.000MiB for chunk-cache and 128.000MiB for networking
INFO  [main] 2021-08-21 06:47:23,330 InboundConnectionInitiator.java:127 - Listening on address: (/172.19.0.2:7000), nic: eth0, encryption: unencrypted
WARN  [main] 2021-08-21 06:47:23,378 SystemKeyspace.java:1130 - No host ID found, created 6611d16d-8384-447f-b0fa-dbdbcdd2a63c (Note: This should happen exactly once per node).
INFO  [main] 2021-08-21 06:47:23,390 StorageService.java:651 - Unable to gossip with any peers but continuing anyway since node is in its own seed list
INFO  [main] 2021-08-21 06:47:23,407 StorageService.java:958 - Starting up server gossip
INFO  [main] 2021-08-21 06:47:23,410 ColumnFamilyStore.java:878 - Enqueuing flush of local: 0.584KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:47:23,417 Memtable.java:469 - Writing Memtable-local@1041898858(0.079KiB serialized bytes, 2 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:47:23,418 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-3-big-Data.db (0.048KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=31458)
INFO  [MemtableFlushWriter:1] 2021-08-21 06:47:23,430 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb_txn_flush_a3b6c630-024b-11ec-8163-d1ebb543407f.log 
INFO  [main] 2021-08-21 06:47:23,466 StorageService.java:1048 - This node will not auto bootstrap because it is configured to be a seed node.

~ $ docker logs -f cassandra
OpenJDK 64-Bit Server VM warning: Option UseConcMarkSweepGC was deprecated in version 9.0 and will likely be removed in a future release.
CompileCommand: dontinline org/apache/cassandra/db/Columns$Serializer.deserializeLargeSubset(Lorg/apache/cassandra/io/util/DataInputPlus;Lorg/apache/cassandra/db/Columns;I)Lorg/apache/cassandra/db/Columns;
CompileCommand: dontinline org/apache/cassandra/db/Columns$Serializer.serializeLargeSubset(Ljava/util/Collection;ILorg/apache/cassandra/db/Columns;ILorg/apache/cassandra/io/util/DataOutputPlus;)V
CompileCommand: dontinline org/apache/cassandra/db/Columns$Serializer.serializeLargeSubsetSize(Ljava/util/Collection;ILorg/apache/cassandra/db/Columns;I)I
CompileCommand: dontinline org/apache/cassandra/db/commitlog/AbstractCommitLogSegmentManager.advanceAllocatingFrom(Lorg/apache/cassandra/db/commitlog/CommitLogSegment;)V
CompileCommand: dontinline org/apache/cassandra/db/transform/BaseIterator.tryGetMoreContents()Z
CompileCommand: dontinline org/apache/cassandra/db/transform/StoppingTransformation.stop()V
CompileCommand: dontinline org/apache/cassandra/db/transform/StoppingTransformation.stopInPartition()V
CompileCommand: dontinline org/apache/cassandra/io/util/BufferedDataOutputStreamPlus.doFlush(I)V
CompileCommand: dontinline org/apache/cassandra/io/util/BufferedDataOutputStreamPlus.writeSlow(JI)V
CompileCommand: dontinline org/apache/cassandra/io/util/RebufferingInputStream.readPrimitiveSlowly(I)J
CompileCommand: exclude org/apache/cassandra/utils/JVMStabilityInspector.forceHeapSpaceOomMaybe(Ljava/lang/OutOfMemoryError;)V
CompileCommand: inline org/apache/cassandra/db/rows/UnfilteredSerializer.serializeRowBody(Lorg/apache/cassandra/db/rows/Row;ILorg/apache/cassandra/db/rows/SerializationHelper;Lorg/apache/cassandra/io/util/DataOutputPlus;)V
CompileCommand: inline org/apache/cassandra/io/util/Memory.checkBounds(JJ)V
CompileCommand: inline org/apache/cassandra/io/util/SafeMemory.checkBounds(JJ)V
CompileCommand: inline org/apache/cassandra/net/FrameDecoderWith8bHeader.decode(Ljava/util/Collection;Lorg/apache/cassandra/net/ShareableBytes;I)V
CompileCommand: inline org/apache/cassandra/service/reads/repair/RowIteratorMergeListener.applyToPartition(ILjava/util/function/Consumer;)V
CompileCommand: inline org/apache/cassandra/utils/AsymmetricOrdering.selectBoundary(Lorg/apache/cassandra/utils/AsymmetricOrdering/Op;II)I
CompileCommand: inline org/apache/cassandra/utils/AsymmetricOrdering.strictnessOfLessThan(Lorg/apache/cassandra/utils/AsymmetricOrdering/Op;)I
CompileCommand: inline org/apache/cassandra/utils/BloomFilter.indexes(Lorg/apache/cassandra/utils/IFilter/FilterKey;)[J
CompileCommand: inline org/apache/cassandra/utils/BloomFilter.setIndexes(JJIJ[J)V
CompileCommand: inline org/apache/cassandra/utils/ByteBufferUtil.compare(Ljava/nio/ByteBuffer;[B)I
CompileCommand: inline org/apache/cassandra/utils/ByteBufferUtil.compare([BLjava/nio/ByteBuffer;)I
CompileCommand: inline org/apache/cassandra/utils/ByteBufferUtil.compareUnsigned(Ljava/nio/ByteBuffer;Ljava/nio/ByteBuffer;)I
CompileCommand: inline org/apache/cassandra/utils/FastByteOperations$UnsafeOperations.compareTo(Ljava/lang/Object;JILjava/lang/Object;JI)I
CompileCommand: inline org/apache/cassandra/utils/FastByteOperations$UnsafeOperations.compareTo(Ljava/lang/Object;JILjava/nio/ByteBuffer;)I
CompileCommand: inline org/apache/cassandra/utils/FastByteOperations$UnsafeOperations.compareTo(Ljava/nio/ByteBuffer;Ljava/nio/ByteBuffer;)I
CompileCommand: inline org/apache/cassandra/utils/memory/BufferPool$LocalPool.tryGetInternal(IZ)Ljava/nio/ByteBuffer;
CompileCommand: inline org/apache/cassandra/utils/vint/VIntCoding.encodeUnsignedVInt(JI)[B
CompileCommand: inline org/apache/cassandra/utils/vint/VIntCoding.encodeUnsignedVInt(JI[B)V
CompileCommand: inline org/apache/cassandra/utils/vint/VIntCoding.writeUnsignedVInt(JLjava/io/DataOutput;)V
CompileCommand: inline org/apache/cassandra/utils/vint/VIntCoding.writeUnsignedVInt(JLjava/nio/ByteBuffer;)V
CompileCommand: inline org/apache/cassandra/utils/vint/VIntCoding.writeVInt(JLjava/io/DataOutput;)V
INFO  [main] 2021-08-21 06:47:20,353 YamlConfigurationLoader.java:93 - Configuration location: file:/etc/cassandra/cassandra.yaml
INFO  [main] 2021-08-21 06:47:20,788 Config.java:691 - Node configuration:[allocate_tokens_for_keyspace=null; allocate_tokens_for_local_replication_factor=3; audit_logging_options=AuditLogOptions{enabled=false, logger='BinAuditLogger', included_keyspaces='', excluded_keyspaces='system,system_schema,system_virtual_schema', included_categories='', excluded_categories='', included_users='', excluded_users='', audit_logs_dir='/opt/cassandra/logs/audit/', archive_command='', roll_cycle='HOURLY', block=true, max_queue_weight=268435456, max_log_size=17179869184}; authenticator=AllowAllAuthenticator; authorizer=AllowAllAuthorizer; auto_bootstrap=true; auto_optimise_full_repair_streams=false; auto_optimise_inc_repair_streams=false; auto_optimise_preview_repair_streams=false; auto_snapshot=true; autocompaction_on_startup_enabled=true; automatic_sstable_upgrade=false; back_pressure_enabled=false; back_pressure_strategy=null; batch_size_fail_threshold_in_kb=50; batch_size_warn_threshold_in_kb=5; batchlog_replay_throttle_in_kb=1024; block_for_peers_in_remote_dcs=false; block_for_peers_timeout_in_secs=10; broadcast_address=172.19.0.2; broadcast_rpc_address=172.19.0.2; buffer_pool_use_heap_if_exhausted=false; cas_contention_timeout_in_ms=1000; cdc_enabled=false; cdc_free_space_check_interval_ms=250; cdc_raw_directory=null; cdc_total_space_in_mb=0; check_for_duplicate_rows_during_compaction=true; check_for_duplicate_rows_during_reads=true; client_encryption_options=<REDACTED>; cluster_name=Test Cluster; column_index_cache_size_in_kb=2; column_index_size_in_kb=64; commit_failure_policy=stop; commitlog_compression=null; commitlog_directory=null; commitlog_max_compression_buffers_in_pool=3; commitlog_periodic_queue_size=-1; commitlog_segment_size_in_mb=32; commitlog_sync=periodic; commitlog_sync_batch_window_in_ms=NaN; commitlog_sync_group_window_in_ms=NaN; commitlog_sync_period_in_ms=10000; commitlog_total_space_in_mb=null; compaction_large_partition_warning_threshold_mb=100; compaction_throughput_mb_per_sec=64; concurrent_compactors=null; concurrent_counter_writes=32; concurrent_materialized_view_builders=1; concurrent_materialized_view_writes=32; concurrent_reads=32; concurrent_replicates=null; concurrent_validations=0; concurrent_writes=32; consecutive_message_errors_threshold=1; corrupted_tombstone_strategy=disabled; counter_cache_keys_to_save=2147483647; counter_cache_save_period=7200; counter_cache_size_in_mb=null; counter_write_request_timeout_in_ms=5000; credentials_cache_max_entries=1000; credentials_update_interval_in_ms=-1; credentials_validity_in_ms=2000; cross_node_timeout=true; data_file_directories=[Ljava.lang.String;@42257bdd; diagnostic_events_enabled=false; disk_access_mode=auto; disk_failure_policy=stop; disk_optimization_estimate_percentile=0.95; disk_optimization_page_cross_chance=0.1; disk_optimization_strategy=ssd; dynamic_snitch=true; dynamic_snitch_badness_threshold=1.0; dynamic_snitch_reset_interval_in_ms=600000; dynamic_snitch_update_interval_in_ms=100; enable_drop_compact_storage=false; enable_materialized_views=false; enable_sasi_indexes=false; enable_scripted_user_defined_functions=false; enable_transient_replication=false; enable_user_defined_functions=false; enable_user_defined_functions_threads=true; endpoint_snitch=SimpleSnitch; file_cache_enabled=false; file_cache_round_up=null; file_cache_size_in_mb=null; flush_compression=fast; full_query_logging_options=FullQueryLoggerOptions{log_dir='', archive_command='', roll_cycle='HOURLY', block=true, max_queue_weight=268435456, max_log_size=17179869184}; gc_log_threshold_in_ms=200; gc_warn_threshold_in_ms=1000; hinted_handoff_disabled_datacenters=[]; hinted_handoff_enabled=true; hinted_handoff_throttle_in_kb=1024; hints_compression=null; hints_directory=null; hints_flush_period_in_ms=10000; ideal_consistency_level=null; incremental_backups=false; index_summary_capacity_in_mb=null; index_summary_resize_interval_in_minutes=60; initial_range_tombstone_list_allocation_size=1; initial_token=null; inter_dc_stream_throughput_outbound_megabits_per_sec=200; inter_dc_tcp_nodelay=false; internode_application_receive_queue_capacity_in_bytes=4194304; internode_application_receive_queue_reserve_endpoint_capacity_in_bytes=134217728; internode_application_receive_queue_reserve_global_capacity_in_bytes=536870912; internode_application_send_queue_capacity_in_bytes=4194304; internode_application_send_queue_reserve_endpoint_capacity_in_bytes=134217728; internode_application_send_queue_reserve_global_capacity_in_bytes=536870912; internode_authenticator=null; internode_compression=dc; internode_max_message_size_in_bytes=null; internode_socket_receive_buffer_size_in_bytes=0; internode_socket_send_buffer_size_in_bytes=0; internode_streaming_tcp_user_timeout_in_ms=300000; internode_tcp_connect_timeout_in_ms=2000; internode_tcp_user_timeout_in_ms=30000; key_cache_keys_to_save=2147483647; key_cache_migrate_during_compaction=true; key_cache_save_period=14400; key_cache_size_in_mb=null; keyspace_count_warn_threshold=40; listen_address=172.19.0.2; listen_interface=null; listen_interface_prefer_ipv6=false; listen_on_broadcast_address=false; local_system_data_file_directory=null; max_concurrent_automatic_sstable_upgrades=1; max_hint_window_in_ms=10800000; max_hints_delivery_threads=2; max_hints_file_size_in_mb=128; max_mutation_size_in_kb=null; max_streaming_retries=3; max_value_size_in_mb=256; memtable_allocation_type=heap_buffers; memtable_cleanup_threshold=null; memtable_flush_writers=0; memtable_heap_space_in_mb=null; memtable_offheap_space_in_mb=null; min_free_space_per_drive_in_mb=50; native_transport_allow_older_protocols=true; native_transport_flush_in_batches_legacy=false; native_transport_idle_timeout_in_ms=0; native_transport_max_concurrent_connections=-1; native_transport_max_concurrent_connections_per_ip=-1; native_transport_max_concurrent_requests_in_bytes=-1; native_transport_max_concurrent_requests_in_bytes_per_ip=-1; native_transport_max_frame_size_in_mb=256; native_transport_max_negotiable_protocol_version=null; native_transport_max_threads=128; native_transport_port=9042; native_transport_port_ssl=null; native_transport_receive_queue_capacity_in_bytes=1048576; network_authorizer=AllowAllNetworkAuthorizer; networking_cache_size_in_mb=null; num_tokens=16; otc_coalescing_enough_coalesced_messages=8; otc_coalescing_strategy=DISABLED; otc_coalescing_window_us=200; partitioner=org.apache.cassandra.dht.Murmur3Partitioner; periodic_commitlog_sync_lag_block_in_ms=null; permissions_cache_max_entries=1000; permissions_update_interval_in_ms=-1; permissions_validity_in_ms=2000; phi_convict_threshold=8.0; prepared_statements_cache_size_mb=null; range_request_timeout_in_ms=10000; range_tombstone_list_growth_factor=1.5; read_request_timeout_in_ms=5000; reject_repair_compaction_threshold=2147483647; repair_command_pool_full_strategy=queue; repair_command_pool_size=0; repair_session_max_tree_depth=null; repair_session_space_in_mb=null; repaired_data_tracking_for_partition_reads_enabled=false; repaired_data_tracking_for_range_reads_enabled=false; report_unconfirmed_repaired_data_mismatches=false; request_timeout_in_ms=10000; role_manager=CassandraRoleManager; roles_cache_max_entries=1000; roles_update_interval_in_ms=-1; roles_validity_in_ms=2000; row_cache_class_name=org.apache.cassandra.cache.OHCProvider; row_cache_keys_to_save=2147483647; row_cache_save_period=0; row_cache_size_in_mb=0; rpc_address=0.0.0.0; rpc_interface=null; rpc_interface_prefer_ipv6=false; rpc_keepalive=true; saved_caches_directory=null; seed_provider=org.apache.cassandra.locator.SimpleSeedProvider{seeds=172.19.0.2}; server_encryption_options=<REDACTED>; slow_query_log_timeout_in_ms=500; snapshot_before_compaction=false; snapshot_links_per_second=0; snapshot_on_duplicate_row_detection=false; snapshot_on_repaired_data_mismatch=false; ssl_storage_port=7001; sstable_preemptive_open_interval_in_mb=50; start_native_transport=true; storage_port=7000; stream_entire_sstables=true; stream_throughput_outbound_megabits_per_sec=200; streaming_connections_per_host=1; streaming_keep_alive_period_in_secs=300; table_count_warn_threshold=150; tombstone_failure_threshold=100000; tombstone_warn_threshold=1000; tracetype_query_ttl=86400; tracetype_repair_ttl=604800; transparent_data_encryption_options=org.apache.cassandra.config.TransparentDataEncryptionOptions@7689ddef; trickle_fsync=false; trickle_fsync_interval_in_kb=10240; truncate_request_timeout_in_ms=60000; unlogged_batch_across_partitions_warn_threshold=10; use_offheap_merkle_trees=true; user_defined_function_fail_timeout=1500; user_defined_function_warn_timeout=500; user_function_timeout_policy=die; validation_preview_purge_head_start_in_sec=3600; windows_timer_interval=1; write_request_timeout_in_ms=2000]
INFO  [main] 2021-08-21 06:47:20,791 DatabaseDescriptor.java:416 - DiskAccessMode 'auto' determined to be mmap, indexAccessMode is mmap
INFO  [main] 2021-08-21 06:47:20,792 DatabaseDescriptor.java:477 - Global memtable on-heap threshold is enabled at 606MB
INFO  [main] 2021-08-21 06:47:20,792 DatabaseDescriptor.java:481 - Global memtable off-heap threshold is enabled at 606MB
INFO  [main] 2021-08-21 06:47:20,906 JMXServerUtils.java:271 - Configured JMX server at: service:jmx:rmi://127.0.0.1/jndi/rmi://127.0.0.1:7199/jmxrmi
INFO  [main] 2021-08-21 06:47:20,911 CassandraDaemon.java:623 - Hostname: cassandra:7000:7001
INFO  [main] 2021-08-21 06:47:20,912 CassandraDaemon.java:630 - JVM vendor/version: OpenJDK 64-Bit Server VM/11.0.11
INFO  [main] 2021-08-21 06:47:20,913 CassandraDaemon.java:631 - Heap size: 2.371GiB/2.371GiB
INFO  [main] 2021-08-21 06:47:20,914 CassandraDaemon.java:636 - CodeHeap 'non-nmethods' Non-heap memory: init = 2555904(2496K) used = 1192832(1164K) committed = 2555904(2496K) max = 5836800(5700K)
INFO  [main] 2021-08-21 06:47:20,924 CassandraDaemon.java:636 - Metaspace Non-heap memory: init = 0(0K) used = 26309840(25693K) committed = 26906624(26276K) max = -1(-1K)
INFO  [main] 2021-08-21 06:47:20,924 CassandraDaemon.java:636 - CodeHeap 'profiled nmethods' Non-heap memory: init = 2555904(2496K) used = 3936256(3844K) committed = 3997696(3904K) max = 122908672(120028K)
INFO  [main] 2021-08-21 06:47:20,925 CassandraDaemon.java:636 - Compressed Class Space Non-heap memory: init = 0(0K) used = 3030440(2959K) committed = 3297280(3220K) max = 1073741824(1048576K)
INFO  [main] 2021-08-21 06:47:20,925 CassandraDaemon.java:636 - Par Eden Space Heap memory: init = 521797632(509568K) used = 146133560(142708K) committed = 521797632(509568K) max = 521797632(509568K)
INFO  [main] 2021-08-21 06:47:20,926 CassandraDaemon.java:636 - Par Survivor Space Heap memory: init = 65208320(63680K) used = 0(0K) committed = 65208320(63680K) max = 65208320(63680K)
INFO  [main] 2021-08-21 06:47:20,926 CassandraDaemon.java:636 - CodeHeap 'non-profiled nmethods' Non-heap memory: init = 2555904(2496K) used = 719744(702K) committed = 2555904(2496K) max = 122912768(120032K)
INFO  [main] 2021-08-21 06:47:20,927 CassandraDaemon.java:636 - CMS Old Gen Heap memory: init = 1958739968(1912832K) used = 0(0K) committed = 1958739968(1912832K) max = 1958739968(1912832K)
INFO  [main] 2021-08-21 06:47:20,927 CassandraDaemon.java:638 - Classpath: /etc/cassandra:/opt/cassandra/lib/HdrHistogram-2.1.9.jar:/opt/cassandra/lib/ST4-4.0.8.jar:/opt/cassandra/lib/airline-0.8.jar:/opt/cassandra/lib/antlr-runtime-3.5.2.jar:/opt/cassandra/lib/apache-cassandra-4.0.0.jar:/opt/cassandra/lib/asm-7.1.jar:/opt/cassandra/lib/caffeine-2.3.5.jar:/opt/cassandra/lib/cassandra-driver-core-3.11.0-shaded.jar:/opt/cassandra/lib/chronicle-bytes-2.20.111.jar:/opt/cassandra/lib/chronicle-core-2.20.126.jar:/opt/cassandra/lib/chronicle-queue-5.20.123.jar:/opt/cassandra/lib/chronicle-threads-2.20.111.jar:/opt/cassandra/lib/chronicle-wire-2.20.117.jar:/opt/cassandra/lib/commons-cli-1.1.jar:/opt/cassandra/lib/commons-codec-1.9.jar:/opt/cassandra/lib/commons-lang3-3.11.jar:/opt/cassandra/lib/commons-math3-3.2.jar:/opt/cassandra/lib/concurrent-trees-2.4.0.jar:/opt/cassandra/lib/ecj-4.6.1.jar:/opt/cassandra/lib/guava-27.0-jre.jar:/opt/cassandra/lib/high-scale-lib-1.0.6.jar:/opt/cassandra/lib/hppc-0.8.1.jar:/opt/cassandra/lib/j2objc-annotations-1.3.jar:/opt/cassandra/lib/jackson-annotations-2.9.10.jar:/opt/cassandra/lib/jackson-core-2.9.10.jar:/opt/cassandra/lib/jackson-databind-2.9.10.8.jar:/opt/cassandra/lib/jamm-0.3.2.jar:/opt/cassandra/lib/java-cup-runtime-11b-20160615.jar:/opt/cassandra/lib/javax.inject-1.jar:/opt/cassandra/lib/jbcrypt-0.3m.jar:/opt/cassandra/lib/jcl-over-slf4j-1.7.25.jar:/opt/cassandra/lib/jcommander-1.30.jar:/opt/cassandra/lib/jctools-core-3.1.0.jar:/opt/cassandra/lib/jflex-1.8.2.jar:/opt/cassandra/lib/jna-5.6.0.jar:/opt/cassandra/lib/json-simple-1.1.jar:/opt/cassandra/lib/jvm-attach-api-1.5.jar:/opt/cassandra/lib/log4j-over-slf4j-1.7.25.jar:/opt/cassandra/lib/logback-classic-1.2.3.jar:/opt/cassandra/lib/logback-core-1.2.3.jar:/opt/cassandra/lib/lz4-java-1.7.1.jar:/opt/cassandra/lib/metrics-core-3.1.5.jar:/opt/cassandra/lib/metrics-jvm-3.1.5.jar:/opt/cassandra/lib/metrics-logback-3.1.5.jar:/opt/cassandra/lib/mxdump-0.14.jar:/opt/cassandra/lib/netty-all-4.1.58.Final.jar:/opt/cassandra/lib/netty-tcnative-boringssl-static-2.0.36.Final.jar:/opt/cassandra/lib/ohc-core-0.5.1.jar:/opt/cassandra/lib/ohc-core-j8-0.5.1.jar:/opt/cassandra/lib/psjava-0.1.19.jar:/opt/cassandra/lib/reporter-config-base-3.0.3.jar:/opt/cassandra/lib/reporter-config3-3.0.3.jar:/opt/cassandra/lib/sigar-1.6.4.jar:/opt/cassandra/lib/sjk-cli-0.14.jar:/opt/cassandra/lib/sjk-core-0.14.jar:/opt/cassandra/lib/sjk-json-0.14.jar:/opt/cassandra/lib/sjk-stacktrace-0.14.jar:/opt/cassandra/lib/slf4j-api-1.7.25.jar:/opt/cassandra/lib/snakeyaml-1.26.jar:/opt/cassandra/lib/snappy-java-1.1.2.6.jar:/opt/cassandra/lib/snowball-stemmer-1.3.0.581.1.jar:/opt/cassandra/lib/stream-2.5.2.jar:/opt/cassandra/lib/zstd-jni-1.3.8-5.jar:/opt/cassandra/lib/jsr223/*/*.jar:
INFO  [main] 2021-08-21 06:47:20,928 CassandraDaemon.java:640 - JVM Arguments: [-ea, -da:net.openhft..., -XX:+UseThreadPriorities, -XX:+HeapDumpOnOutOfMemoryError, -Xss256k, -XX:+AlwaysPreTouch, -XX:-UseBiasedLocking, -XX:+UseTLAB, -XX:+ResizeTLAB, -XX:+UseNUMA, -XX:+PerfDisableSharedMem, -Djava.net.preferIPv4Stack=true, -XX:+UseConcMarkSweepGC, -XX:+CMSParallelRemarkEnabled, -XX:SurvivorRatio=8, -XX:MaxTenuringThreshold=1, -XX:CMSInitiatingOccupancyFraction=75, -XX:+UseCMSInitiatingOccupancyOnly, -XX:CMSWaitDuration=10000, -XX:+CMSParallelInitialMarkEnabled, -XX:+CMSEdenChunksRecordAlways, -XX:+CMSClassUnloadingEnabled, -Djdk.attach.allowAttachSelf=true, --add-exports=java.base/jdk.internal.misc=ALL-UNNAMED, --add-exports=java.base/jdk.internal.ref=ALL-UNNAMED, --add-exports=java.base/sun.nio.ch=ALL-UNNAMED, --add-exports=java.management.rmi/com.sun.jmx.remote.internal.rmi=ALL-UNNAMED, --add-exports=java.rmi/sun.rmi.registry=ALL-UNNAMED, --add-exports=java.rmi/sun.rmi.server=ALL-UNNAMED, --add-exports=java.sql/java.sql=ALL-UNNAMED, --add-opens=java.base/java.lang.module=ALL-UNNAMED, --add-opens=java.base/jdk.internal.loader=ALL-UNNAMED, --add-opens=java.base/jdk.internal.ref=ALL-UNNAMED, --add-opens=java.base/jdk.internal.reflect=ALL-UNNAMED, --add-opens=java.base/jdk.internal.math=ALL-UNNAMED, --add-opens=java.base/jdk.internal.module=ALL-UNNAMED, --add-opens=java.base/jdk.internal.util.jar=ALL-UNNAMED, --add-opens=jdk.management/com.sun.management.internal=ALL-UNNAMED, -Dio.netty.tryReflectionSetAccessible=true, -Xlog:gc=info,heap*=trace,age*=debug,safepoint=info,promotion*=trace:file=/opt/cassandra/logs/gc.log:time,uptime,pid,tid,level:filecount=10,filesize=10485760, -Xms2490M, -Xmx2490M, -Xmn622M, -XX:+UseCondCardMark, -XX:CompileCommandFile=/etc/cassandra/hotspot_compiler, -javaagent:/opt/cassandra/lib/jamm-0.3.2.jar, -Dcassandra.jmx.local.port=7199, -Dcom.sun.management.jmxremote.authenticate=false, -Dcom.sun.management.jmxremote.password.file=/etc/cassandra/jmxremote.password, -Djava.library.path=/opt/cassandra/lib/sigar-bin, -Dcassandra.libjemalloc=/usr/local/lib/libjemalloc.so, -XX:OnOutOfMemoryError=kill -9 %p, -Dlogback.configurationFile=logback.xml, -Dcassandra.logdir=/opt/cassandra/logs, -Dcassandra.storagedir=/opt/cassandra/data, -Dcassandra-foreground=yes]
WARN  [main] 2021-08-21 06:47:20,988 NativeLibrary.java:201 - Unable to lock JVM memory (ENOMEM). This can result in part of the JVM being swapped out, especially with mmapped I/O enabled. Increase RLIMIT_MEMLOCK.
INFO  [main] 2021-08-21 06:47:21,035 MonotonicClock.java:199 - Scheduling approximate time conversion task with an interval of 10000 milliseconds
INFO  [main] 2021-08-21 06:47:21,038 MonotonicClock.java:335 - Scheduling approximate time-check task with a precision of 2 milliseconds
INFO  [main] 2021-08-21 06:47:21,040 StartupChecks.java:147 - jemalloc seems to be preloaded from /usr/local/lib/libjemalloc.so
WARN  [main] 2021-08-21 06:47:21,041 StartupChecks.java:187 - JMX is not enabled to receive remote connections. Please see cassandra-env.sh for more info.
INFO  [main] 2021-08-21 06:47:21,042 SigarLibrary.java:44 - Initializing SIGAR library
WARN  [main] 2021-08-21 06:47:21,051 SigarLibrary.java:174 - Cassandra server running in degraded mode. Is swap disabled? : false,  Address space adequate? : true,  nofile limit adequate? : true, nproc limit adequate? : true 
WARN  [main] 2021-08-21 06:47:21,052 StartupChecks.java:329 - Maximum number of memory map areas per process (vm.max_map_count) 262144 is too low, recommended value: 1048575, you can change it with sysctl.
INFO  [main] 2021-08-21 06:47:21,441 Keyspace.java:386 - Creating replication strategy system params KeyspaceParams{durable_writes=true, replication=ReplicationParams{class=org.apache.cassandra.locator.LocalStrategy}}
INFO  [main] 2021-08-21 06:47:21,482 ColumnFamilyStore.java:385 - Initializing system.IndexInfo
INFO  [main] 2021-08-21 06:47:22,012 ColumnFamilyStore.java:385 - Initializing system.batches
INFO  [main] 2021-08-21 06:47:22,024 ColumnFamilyStore.java:385 - Initializing system.paxos
INFO  [main] 2021-08-21 06:47:22,040 ColumnFamilyStore.java:385 - Initializing system.local
INFO  [main] 2021-08-21 06:47:22,048 ColumnFamilyStore.java:385 - Initializing system.peers_v2
INFO  [main] 2021-08-21 06:47:22,060 ColumnFamilyStore.java:385 - Initializing system.peers
INFO  [main] 2021-08-21 06:47:22,069 ColumnFamilyStore.java:385 - Initializing system.peer_events_v2
INFO  [main] 2021-08-21 06:47:22,079 ColumnFamilyStore.java:385 - Initializing system.peer_events
INFO  [main] 2021-08-21 06:47:22,088 ColumnFamilyStore.java:385 - Initializing system.compaction_history
INFO  [main] 2021-08-21 06:47:22,097 ColumnFamilyStore.java:385 - Initializing system.sstable_activity
INFO  [main] 2021-08-21 06:47:22,106 ColumnFamilyStore.java:385 - Initializing system.size_estimates
INFO  [main] 2021-08-21 06:47:22,115 ColumnFamilyStore.java:385 - Initializing system.table_estimates
INFO  [main] 2021-08-21 06:47:22,124 ColumnFamilyStore.java:385 - Initializing system.available_ranges_v2
INFO  [main] 2021-08-21 06:47:22,133 ColumnFamilyStore.java:385 - Initializing system.available_ranges
INFO  [main] 2021-08-21 06:47:22,142 ColumnFamilyStore.java:385 - Initializing system.transferred_ranges_v2
INFO  [main] 2021-08-21 06:47:22,151 ColumnFamilyStore.java:385 - Initializing system.transferred_ranges
INFO  [main] 2021-08-21 06:47:22,160 ColumnFamilyStore.java:385 - Initializing system.view_builds_in_progress
INFO  [main] 2021-08-21 06:47:22,169 ColumnFamilyStore.java:385 - Initializing system.built_views
INFO  [main] 2021-08-21 06:47:22,177 ColumnFamilyStore.java:385 - Initializing system.prepared_statements
INFO  [main] 2021-08-21 06:47:22,186 ColumnFamilyStore.java:385 - Initializing system.repairs
INFO  [main] 2021-08-21 06:47:22,391 QueryProcessor.java:106 - Initialized prepared statement caches with 10 MB
INFO  [main] 2021-08-21 06:47:22,518 Keyspace.java:386 - Creating replication strategy system_schema params KeyspaceParams{durable_writes=true, replication=ReplicationParams{class=org.apache.cassandra.locator.LocalStrategy}}
INFO  [main] 2021-08-21 06:47:22,522 ColumnFamilyStore.java:385 - Initializing system_schema.keyspaces
INFO  [main] 2021-08-21 06:47:22,530 ColumnFamilyStore.java:385 - Initializing system_schema.tables
INFO  [main] 2021-08-21 06:47:22,538 ColumnFamilyStore.java:385 - Initializing system_schema.columns
INFO  [main] 2021-08-21 06:47:22,547 ColumnFamilyStore.java:385 - Initializing system_schema.triggers
INFO  [main] 2021-08-21 06:47:22,554 ColumnFamilyStore.java:385 - Initializing system_schema.dropped_columns
INFO  [main] 2021-08-21 06:47:22,562 ColumnFamilyStore.java:385 - Initializing system_schema.views
INFO  [main] 2021-08-21 06:47:22,570 ColumnFamilyStore.java:385 - Initializing system_schema.types
INFO  [main] 2021-08-21 06:47:22,578 ColumnFamilyStore.java:385 - Initializing system_schema.functions
INFO  [main] 2021-08-21 06:47:22,585 ColumnFamilyStore.java:385 - Initializing system_schema.aggregates
INFO  [main] 2021-08-21 06:47:22,593 ColumnFamilyStore.java:385 - Initializing system_schema.indexes
INFO  [main] 2021-08-21 06:47:22,668 SystemKeyspaceMigrator40.java:76 - system.peers_v2 table was empty, migrating legacy system.peers, if this fails you should fix the issue and then truncate system.peers_v2 to have it try again.
INFO  [main] 2021-08-21 06:47:22,675 SystemKeyspaceMigrator40.java:100 - Migrating rows from legacy system.peers to system.peers_v2
INFO  [main] 2021-08-21 06:47:22,680 SystemKeyspaceMigrator40.java:119 - Migrated 0 rows from legacy system.peers to system.peers_v2
INFO  [main] 2021-08-21 06:47:22,680 SystemKeyspaceMigrator40.java:129 - system.peer_events_v2 table was empty, migrating legacy system.peer_events to system.peer_events_v2
INFO  [main] 2021-08-21 06:47:22,681 SystemKeyspaceMigrator40.java:152 - Migrated 0 rows from legacy system.peer_events to system.peer_events_v2
INFO  [main] 2021-08-21 06:47:22,682 SystemKeyspaceMigrator40.java:162 - system.transferred_ranges_v2 table was empty, migrating legacy system.transferred_ranges to system.transferred_ranges_v2
INFO  [main] 2021-08-21 06:47:22,684 SystemKeyspaceMigrator40.java:190 - Migrated 0 rows from legacy system.transferred_ranges to system.transferred_ranges_v2
INFO  [main] 2021-08-21 06:47:22,684 SystemKeyspaceMigrator40.java:200 - system.available_ranges_v2 table was empty, migrating legacy system.available_ranges to system.available_ranges_v2
INFO  [main] 2021-08-21 06:47:22,685 SystemKeyspaceMigrator40.java:226 - Migrated 0 rows from legacy system.available_ranges to system.available_ranges_v2
INFO  [main] 2021-08-21 06:47:22,685 StorageService.java:836 - Populating token metadata from system tables
INFO  [main] 2021-08-21 06:47:22,709 StorageService.java:830 - Token metadata: 
INFO  [main] 2021-08-21 06:47:22,749 CacheService.java:100 - Initializing key cache with capacity of 100 MBs.
INFO  [main] 2021-08-21 06:47:22,762 CacheService.java:122 - Initializing row cache with capacity of 0 MBs
INFO  [main] 2021-08-21 06:47:22,764 CacheService.java:151 - Initializing counter cache with capacity of 50 MBs
INFO  [main] 2021-08-21 06:47:22,766 CacheService.java:162 - Scheduling counter cache save to every 7200 seconds (going to save all keys).
INFO  [main] 2021-08-21 06:47:22,792 CommitLog.java:168 - No commitlog files found; skipping replay
INFO  [main] 2021-08-21 06:47:22,792 StorageService.java:836 - Populating token metadata from system tables
INFO  [main] 2021-08-21 06:47:22,804 StorageService.java:830 - Token metadata: 
INFO  [main] 2021-08-21 06:47:22,922 ColumnFamilyStore.java:2242 - Truncating system.size_estimates
INFO  [main] 2021-08-21 06:47:22,946 ColumnFamilyStore.java:2279 - Truncating system.size_estimates with truncatedAt=1629528442928
INFO  [main] 2021-08-21 06:47:22,980 ColumnFamilyStore.java:878 - Enqueuing flush of local: 2.199KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:47:23,041 Memtable.java:469 - Writing Memtable-local@995377569(0.429KiB serialized bytes, 3 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:47:23,044 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-1-big-Data.db (0.224KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=31191)
INFO  [MemtableFlushWriter:1] 2021-08-21 06:47:23,087 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb_txn_flush_a3759e80-024b-11ec-8163-d1ebb543407f.log 
INFO  [main] 2021-08-21 06:47:23,098 ColumnFamilyStore.java:2306 - Truncate of system.size_estimates is complete
INFO  [main] 2021-08-21 06:47:23,098 ColumnFamilyStore.java:2242 - Truncating system.table_estimates
INFO  [main] 2021-08-21 06:47:23,099 ColumnFamilyStore.java:2279 - Truncating system.table_estimates with truncatedAt=1629528443099
INFO  [main] 2021-08-21 06:47:23,102 ColumnFamilyStore.java:878 - Enqueuing flush of local: 0.576KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:47:23,107 Memtable.java:469 - Writing Memtable-local@1210431984(0.091KiB serialized bytes, 1 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:47:23,108 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-2-big-Data.db (0.063KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=31302)
INFO  [MemtableFlushWriter:2] 2021-08-21 06:47:23,118 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb_txn_flush_a3879fe0-024b-11ec-8163-d1ebb543407f.log 
INFO  [main] 2021-08-21 06:47:23,120 ColumnFamilyStore.java:2306 - Truncate of system.table_estimates is complete
INFO  [main] 2021-08-21 06:47:23,124 QueryProcessor.java:150 - Preloaded 0 prepared statements
INFO  [main] 2021-08-21 06:47:23,124 StorageService.java:734 - Cassandra version: 4.0.0
INFO  [main] 2021-08-21 06:47:23,124 StorageService.java:735 - CQL version: 3.4.5
INFO  [main] 2021-08-21 06:47:23,125 StorageService.java:736 - Native protocol supported versions: 3/v3, 4/v4, 5/v5, 6/v6-beta (default: 5/v5)
INFO  [main] 2021-08-21 06:47:23,161 IndexSummaryManager.java:87 - Initializing index summary manager with a memory pool size of 121 MB and a resize interval of 60 minutes
INFO  [main] 2021-08-21 06:47:23,163 StorageService.java:753 - Loading persisted ring state
INFO  [main] 2021-08-21 06:47:23,163 StorageService.java:836 - Populating token metadata from system tables
INFO  [main] 2021-08-21 06:47:23,192 BufferPools.java:49 - Global buffer pool limit is 512.000MiB for chunk-cache and 128.000MiB for networking
INFO  [main] 2021-08-21 06:47:23,330 InboundConnectionInitiator.java:127 - Listening on address: (/172.19.0.2:7000), nic: eth0, encryption: unencrypted
WARN  [main] 2021-08-21 06:47:23,378 SystemKeyspace.java:1130 - No host ID found, created 6611d16d-8384-447f-b0fa-dbdbcdd2a63c (Note: This should happen exactly once per node).
INFO  [main] 2021-08-21 06:47:23,390 StorageService.java:651 - Unable to gossip with any peers but continuing anyway since node is in its own seed list
INFO  [main] 2021-08-21 06:47:23,407 StorageService.java:958 - Starting up server gossip
INFO  [main] 2021-08-21 06:47:23,410 ColumnFamilyStore.java:878 - Enqueuing flush of local: 0.584KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:47:23,417 Memtable.java:469 - Writing Memtable-local@1041898858(0.079KiB serialized bytes, 2 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:47:23,418 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-3-big-Data.db (0.048KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=31458)
INFO  [MemtableFlushWriter:1] 2021-08-21 06:47:23,430 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb_txn_flush_a3b6c630-024b-11ec-8163-d1ebb543407f.log 
INFO  [main] 2021-08-21 06:47:23,466 StorageService.java:1048 - This node will not auto bootstrap because it is configured to be a seed node.
INFO  [main] 2021-08-21 06:47:53,452 Gossiper.java:2171 - Waiting for gossip to settle...
INFO  [main] 2021-08-21 06:48:01,422 Gossiper.java:2202 - No gossip backlog; proceeding
INFO  [main] 2021-08-21 06:48:01,423 Gossiper.java:2171 - Waiting for gossip to settle...
INFO  [main] 2021-08-21 06:48:09,429 Gossiper.java:2202 - No gossip backlog; proceeding
INFO  [main] 2021-08-21 06:48:09,434 NetworkTopologyStrategy.java:88 - Configured datacenter replicas are datacenter1:rf(3)
INFO  [main] 2021-08-21 06:48:09,437 TokenAllocatorFactory.java:44 - Using ReplicationAwareTokenAllocator.
INFO  [main] 2021-08-21 06:48:09,476 TokenAllocation.java:106 - Selected tokens [7126507894872445885, -111828670109022814, -4922178629350922248, 4235463513488371047, -7519347377564079621, -2047502428292396830, 2399940176133593237, -9109351930077978259, 6047135087424844227, -3143544328527335119, -5900324081867036323, 1328439559793560424, 8370027900553037857, -956205317600184570, 3417791580876020252, 5311219394713950586]
INFO  [MigrationStage:1] 2021-08-21 06:48:09,505 ColumnFamilyStore.java:878 - Enqueuing flush of columns: 200.087KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,511 Memtable.java:469 - Writing Memtable-columns@1189240452(41.994KiB serialized bytes, 277 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,526 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system_schema/columns-24101c25a2ae3af787c1b40ee1aca33f/nb-1-big-Data.db (20.847KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42076)
INFO  [MemtableFlushWriter:2] 2021-08-21 06:48:09,542 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system_schema/columns-24101c25a2ae3af787c1b40ee1aca33f/nb_txn_flush_bf305020-024b-11ec-8163-d1ebb543407f.log 
INFO  [MigrationStage:1] 2021-08-21 06:48:09,545 ColumnFamilyStore.java:878 - Enqueuing flush of dropped_columns: 1.081KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,552 Memtable.java:469 - Writing Memtable-dropped_columns@1202404485(0.120KiB serialized bytes, 3 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,553 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system_schema/dropped_columns-5e7583b5f3f43af19a39b7e1d6f5f11f/nb-1-big-Data.db (0.097KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42076)
INFO  [MemtableFlushWriter:1] 2021-08-21 06:48:09,564 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system_schema/dropped_columns-5e7583b5f3f43af19a39b7e1d6f5f11f/nb_txn_flush_bf364390-024b-11ec-8163-d1ebb543407f.log 
INFO  [MigrationStage:1] 2021-08-21 06:48:09,566 ColumnFamilyStore.java:878 - Enqueuing flush of triggers: 0.513KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,572 Memtable.java:469 - Writing Memtable-triggers@1121833600(0.016KiB serialized bytes, 2 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,572 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system_schema/triggers-4df70b666b05325195a132b54005fd48/nb-1-big-Data.db (0.048KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42084)
INFO  [MemtableFlushWriter:2] 2021-08-21 06:48:09,583 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system_schema/triggers-4df70b666b05325195a132b54005fd48/nb_txn_flush_bf399ef0-024b-11ec-8163-d1ebb543407f.log 
INFO  [MigrationStage:1] 2021-08-21 06:48:09,585 ColumnFamilyStore.java:878 - Enqueuing flush of types: 0.513KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,590 Memtable.java:469 - Writing Memtable-types@774019394(0.016KiB serialized bytes, 2 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,591 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system_schema/types-5a8b1ca866023f77a0459273d308917a/nb-1-big-Data.db (0.048KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42084)
INFO  [MemtableFlushWriter:1] 2021-08-21 06:48:09,602 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system_schema/types-5a8b1ca866023f77a0459273d308917a/nb_txn_flush_bf3c5e10-024b-11ec-8163-d1ebb543407f.log 
INFO  [MigrationStage:1] 2021-08-21 06:48:09,605 ColumnFamilyStore.java:878 - Enqueuing flush of functions: 0.513KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,610 Memtable.java:469 - Writing Memtable-functions@132076735(0.016KiB serialized bytes, 2 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,611 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system_schema/functions-96489b7980be3e14a70166a0b9159450/nb-1-big-Data.db (0.048KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42084)
INFO  [MemtableFlushWriter:2] 2021-08-21 06:48:09,624 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system_schema/functions-96489b7980be3e14a70166a0b9159450/nb_txn_flush_bf3f6b50-024b-11ec-8163-d1ebb543407f.log 
INFO  [MigrationStage:1] 2021-08-21 06:48:09,626 ColumnFamilyStore.java:878 - Enqueuing flush of aggregates: 0.513KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,631 Memtable.java:469 - Writing Memtable-aggregates@854544294(0.016KiB serialized bytes, 2 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,632 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system_schema/aggregates-924c55872e3a345bb10c12f37c1ba895/nb-1-big-Data.db (0.048KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42084)
INFO  [MemtableFlushWriter:1] 2021-08-21 06:48:09,643 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system_schema/aggregates-924c55872e3a345bb10c12f37c1ba895/nb_txn_flush_bf42c6b0-024b-11ec-8163-d1ebb543407f.log 
INFO  [MigrationStage:1] 2021-08-21 06:48:09,645 ColumnFamilyStore.java:878 - Enqueuing flush of indexes: 0.513KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,650 Memtable.java:469 - Writing Memtable-indexes@1657833357(0.016KiB serialized bytes, 2 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,651 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system_schema/indexes-0feb57ac311f382fba6d9024d305702f/nb-1-big-Data.db (0.048KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42084)
INFO  [MemtableFlushWriter:2] 2021-08-21 06:48:09,662 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system_schema/indexes-0feb57ac311f382fba6d9024d305702f/nb_txn_flush_bf4585d0-024b-11ec-8163-d1ebb543407f.log 
INFO  [MigrationStage:1] 2021-08-21 06:48:09,664 ColumnFamilyStore.java:878 - Enqueuing flush of tables: 92.661KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,670 Memtable.java:469 - Writing Memtable-tables@1559291356(28.858KiB serialized bytes, 42 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,672 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system_schema/tables-afddfb9dbc1e30688056eed6c302ba09/nb-1-big-Data.db (17.879KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42084)
INFO  [MemtableFlushWriter:1] 2021-08-21 06:48:09,683 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system_schema/tables-afddfb9dbc1e30688056eed6c302ba09/nb_txn_flush_bf489310-024b-11ec-8163-d1ebb543407f.log 
INFO  [MigrationStage:1] 2021-08-21 06:48:09,686 ColumnFamilyStore.java:878 - Enqueuing flush of views: 0.513KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,691 Memtable.java:469 - Writing Memtable-views@915600173(0.016KiB serialized bytes, 2 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,692 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system_schema/views-9786ac1cdd583201a7cdad556410c985/nb-1-big-Data.db (0.048KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42084)
INFO  [MemtableFlushWriter:2] 2021-08-21 06:48:09,704 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system_schema/views-9786ac1cdd583201a7cdad556410c985/nb_txn_flush_bf4bc760-024b-11ec-8163-d1ebb543407f.log 
INFO  [MigrationStage:1] 2021-08-21 06:48:09,706 ColumnFamilyStore.java:878 - Enqueuing flush of keyspaces: 3.248KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,711 Memtable.java:469 - Writing Memtable-keyspaces@1117894099(0.673KiB serialized bytes, 7 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,712 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system_schema/keyspaces-abac5682dea631c5b535b3d6cffd0fb6/nb-1-big-Data.db (0.556KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42084)
INFO  [MemtableFlushWriter:1] 2021-08-21 06:48:09,724 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system_schema/keyspaces-abac5682dea631c5b535b3d6cffd0fb6/nb_txn_flush_bf4efbb0-024b-11ec-8163-d1ebb543407f.log 
INFO  [MigrationStage:1] 2021-08-21 06:48:09,793 Keyspace.java:386 - Creating replication strategy system_auth params KeyspaceParams{durable_writes=true, replication=ReplicationParams{class=org.apache.cassandra.locator.SimpleStrategy, replication_factor=1}}
INFO  [MigrationStage:1] 2021-08-21 06:48:09,796 ColumnFamilyStore.java:385 - Initializing system_auth.network_permissions
INFO  [MigrationStage:1] 2021-08-21 06:48:09,804 ColumnFamilyStore.java:385 - Initializing system_auth.resource_role_permissons_index
INFO  [MigrationStage:1] 2021-08-21 06:48:09,811 ColumnFamilyStore.java:385 - Initializing system_auth.role_members
INFO  [MigrationStage:1] 2021-08-21 06:48:09,818 ColumnFamilyStore.java:385 - Initializing system_auth.role_permissions
INFO  [MigrationStage:1] 2021-08-21 06:48:09,824 ColumnFamilyStore.java:385 - Initializing system_auth.roles
INFO  [MigrationStage:1] 2021-08-21 06:48:09,832 Keyspace.java:386 - Creating replication strategy system_distributed params KeyspaceParams{durable_writes=true, replication=ReplicationParams{class=org.apache.cassandra.locator.SimpleStrategy, replication_factor=3}}
INFO  [MigrationStage:1] 2021-08-21 06:48:09,835 ColumnFamilyStore.java:385 - Initializing system_distributed.parent_repair_history
INFO  [MigrationStage:1] 2021-08-21 06:48:09,842 ColumnFamilyStore.java:385 - Initializing system_distributed.repair_history
INFO  [MigrationStage:1] 2021-08-21 06:48:09,849 ColumnFamilyStore.java:385 - Initializing system_distributed.view_build_status
INFO  [MigrationStage:1] 2021-08-21 06:48:09,854 Keyspace.java:386 - Creating replication strategy system_traces params KeyspaceParams{durable_writes=true, replication=ReplicationParams{class=org.apache.cassandra.locator.SimpleStrategy, replication_factor=2}}
INFO  [MigrationStage:1] 2021-08-21 06:48:09,857 ColumnFamilyStore.java:385 - Initializing system_traces.events
INFO  [MigrationStage:1] 2021-08-21 06:48:09,863 ColumnFamilyStore.java:385 - Initializing system_traces.sessions
INFO  [main] 2021-08-21 06:48:09,885 StorageService.java:1619 - JOINING: Finish joining ring
INFO  [main] 2021-08-21 06:48:09,888 ColumnFamilyStore.java:878 - Enqueuing flush of local: 0.604KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,895 Memtable.java:469 - Writing Memtable-local@444038829(0.084KiB serialized bytes, 3 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:2] 2021-08-21 06:48:09,896 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-4-big-Data.db (0.058KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42240)
INFO  [MemtableFlushWriter:2] 2021-08-21 06:48:09,908 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb_txn_flush_bf6ac110-024b-11ec-8163-d1ebb543407f.log 
INFO  [main] 2021-08-21 06:48:09,919 ColumnFamilyStore.java:878 - Enqueuing flush of local: 2.854KiB (0%) on-heap, 0.000KiB (0%) off-heap
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,924 Memtable.java:469 - Writing Memtable-local@2029247564(0.593KiB serialized bytes, 1 ops, 0%/0% of on/off-heap limit), flushed range = (null, null]
INFO  [PerDiskMemtableFlushWriter_0:1] 2021-08-21 06:48:09,925 Memtable.java:498 - Completed flushing /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-5-big-Data.db (0.361KiB) for commitlog position CommitLogPosition(segmentId=1629528441028, position=42645)
INFO  [MemtableFlushWriter:1] 2021-08-21 06:48:09,936 LogTransaction.java:240 - Unfinished transaction log, deleting /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb_txn_flush_bf6f7c00-024b-11ec-8163-d1ebb543407f.log 
INFO  [main] 2021-08-21 06:48:09,950 StorageService.java:2737 - Node /172.19.0.2:7000 state jump to NORMAL
INFO  [main] 2021-08-21 06:48:09,952 Gossiper.java:2171 - Waiting for gossip to settle...
INFO  [main] 2021-08-21 06:48:17,955 Gossiper.java:2202 - No gossip backlog; proceeding
INFO  [main] 2021-08-21 06:48:17,983 NativeTransportService.java:130 - Using Netty Version: [netty-buffer=netty-buffer-4.1.58.Final.10b03e6, netty-codec=netty-codec-4.1.58.Final.10b03e6, netty-codec-dns=netty-codec-dns-4.1.58.Final.10b03e6, netty-codec-haproxy=netty-codec-haproxy-4.1.58.Final.10b03e6, netty-codec-http=netty-codec-http-4.1.58.Final.10b03e6, netty-codec-http2=netty-codec-http2-4.1.58.Final.10b03e6, netty-codec-memcache=netty-codec-memcache-4.1.58.Final.10b03e6, netty-codec-mqtt=netty-codec-mqtt-4.1.58.Final.10b03e6, netty-codec-redis=netty-codec-redis-4.1.58.Final.10b03e6, netty-codec-smtp=netty-codec-smtp-4.1.58.Final.10b03e6, netty-codec-socks=netty-codec-socks-4.1.58.Final.10b03e6, netty-codec-stomp=netty-codec-stomp-4.1.58.Final.10b03e6, netty-codec-xml=netty-codec-xml-4.1.58.Final.10b03e6, netty-common=netty-common-4.1.58.Final.10b03e6, netty-handler=netty-handler-4.1.58.Final.10b03e6, netty-handler-proxy=netty-handler-proxy-4.1.58.Final.10b03e6, netty-resolver=netty-resolver-4.1.58.Final.10b03e6, netty-resolver-dns=netty-resolver-dns-4.1.58.Final.10b03e6, netty-resolver-dns-native-macos=netty-resolver-dns-native-macos-4.1.58.Final.10b03e65f1, netty-transport=netty-transport-4.1.58.Final.10b03e6, netty-transport-native-epoll=netty-transport-native-epoll-4.1.58.Final.10b03e6, netty-transport-native-kqueue=netty-transport-native-kqueue-4.1.58.Final.10b03e65f1, netty-transport-native-unix-common=netty-transport-native-unix-common-4.1.58.Final.10b03e6, netty-transport-rxtx=netty-transport-rxtx-4.1.58.Final.10b03e6, netty-transport-sctp=netty-transport-sctp-4.1.58.Final.10b03e6, netty-transport-udt=netty-transport-udt-4.1.58.Final.10b03e6]
INFO  [CompactionExecutor:2] 2021-08-21 06:48:17,989 CompactionTask.java:150 - Compacting (c43d7ed0-024b-11ec-8163-d1ebb543407f) [/var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-5-big-Data.db:level=0, /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-2-big-Data.db:level=0, /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-1-big-Data.db:level=0, /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-3-big-Data.db:level=0, /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-4-big-Data.db:level=0, ]
INFO  [main] 2021-08-21 06:48:17,995 NativeTransportService.java:68 - Netty using native Epoll event loop
INFO  [main] 2021-08-21 06:48:18,035 PipelineConfigurator.java:124 - Using Netty Version: [netty-buffer=netty-buffer-4.1.58.Final.10b03e6, netty-codec=netty-codec-4.1.58.Final.10b03e6, netty-codec-dns=netty-codec-dns-4.1.58.Final.10b03e6, netty-codec-haproxy=netty-codec-haproxy-4.1.58.Final.10b03e6, netty-codec-http=netty-codec-http-4.1.58.Final.10b03e6, netty-codec-http2=netty-codec-http2-4.1.58.Final.10b03e6, netty-codec-memcache=netty-codec-memcache-4.1.58.Final.10b03e6, netty-codec-mqtt=netty-codec-mqtt-4.1.58.Final.10b03e6, netty-codec-redis=netty-codec-redis-4.1.58.Final.10b03e6, netty-codec-smtp=netty-codec-smtp-4.1.58.Final.10b03e6, netty-codec-socks=netty-codec-socks-4.1.58.Final.10b03e6, netty-codec-stomp=netty-codec-stomp-4.1.58.Final.10b03e6, netty-codec-xml=netty-codec-xml-4.1.58.Final.10b03e6, netty-common=netty-common-4.1.58.Final.10b03e6, netty-handler=netty-handler-4.1.58.Final.10b03e6, netty-handler-proxy=netty-handler-proxy-4.1.58.Final.10b03e6, netty-resolver=netty-resolver-4.1.58.Final.10b03e6, netty-resolver-dns=netty-resolver-dns-4.1.58.Final.10b03e6, netty-resolver-dns-native-macos=netty-resolver-dns-native-macos-4.1.58.Final.10b03e65f1, netty-transport=netty-transport-4.1.58.Final.10b03e6, netty-transport-native-epoll=netty-transport-native-epoll-4.1.58.Final.10b03e6, netty-transport-native-kqueue=netty-transport-native-kqueue-4.1.58.Final.10b03e65f1, netty-transport-native-unix-common=netty-transport-native-unix-common-4.1.58.Final.10b03e6, netty-transport-rxtx=netty-transport-rxtx-4.1.58.Final.10b03e6, netty-transport-sctp=netty-transport-sctp-4.1.58.Final.10b03e6, netty-transport-udt=netty-transport-udt-4.1.58.Final.10b03e6]
INFO  [main] 2021-08-21 06:48:18,035 PipelineConfigurator.java:125 - Starting listening for CQL clients on /0.0.0.0:9042 (unencrypted)...
INFO  [main] 2021-08-21 06:48:18,041 CassandraDaemon.java:780 - Startup complete
INFO  [CompactionExecutor:2] 2021-08-21 06:48:18,058 CompactionTask.java:245 - Compacted (c43d7ed0-024b-11ec-8163-d1ebb543407f) 5 sstables to [/var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-6-big,] to level=0.  0.773KiB to 0.629KiB (~81% of original) in 66ms.  Read Throughput = 11.639KiB/s, Write Throughput = 9.464KiB/s, Row Throughput = ~2/s.  5 total partitions merged to 1.  Partition merge counts were {5:1, }
INFO  [NonPeriodicTasks:1] 2021-08-21 06:48:18,060 SSTable.java:111 - Deleting sstable: /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-5-big
INFO  [NonPeriodicTasks:1] 2021-08-21 06:48:18,062 SSTable.java:111 - Deleting sstable: /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-2-big
INFO  [NonPeriodicTasks:1] 2021-08-21 06:48:18,063 SSTable.java:111 - Deleting sstable: /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-1-big
INFO  [NonPeriodicTasks:1] 2021-08-21 06:48:18,065 SSTable.java:111 - Deleting sstable: /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-3-big
INFO  [NonPeriodicTasks:1] 2021-08-21 06:48:18,067 SSTable.java:111 - Deleting sstable: /var/lib/cassandra/data/system/local-7ad54392bcdd35a684174e047860b377/nb-4-big
INFO  [OptionalTasks:1] 2021-08-21 06:48:20,075 CassandraRoleManager.java:338 - Created default superuser role 'cassandra'
```

```bash
cassandra-stuff $ docker run --rm --network cassandra -v "$(pwd)/exploring/data.cql:/scripts/data.cql" -e CQLSH_HOST=cassandra -e CQLSH_PORT=9042 nuvo/docker-cqlsh
Unable to find image 'nuvo/docker-cqlsh:latest' locally
latest: Pulling from nuvo/docker-cqlsh
cd784148e348: Pull complete 
30f71ecab593: Pull complete 
ed606575a835: Pull complete 
9c862b3c365f: Pull complete 
a5d45fa50c31: Pull complete 
9a1e1cb30c66: Pull complete 
b88bf3f8b15b: Pull complete 
Digest: sha256:410c040df719f9dbb07708c25b5430a22e570c4914084976f0b7dede329fab69
Status: Downloaded newer image for nuvo/docker-cqlsh:latest
Checking connection to cassandra...
Can't establish connection, will retry again in 1 sconds
Can't establish connection, will retry again in 2 sconds
Can't establish connection, will retry again in 3 sconds
Can't establish connection, will retry again in 4 sconds
Can't establish connection, will retry again in 5 sconds
Failed to connect to cassandra at cassandra:9042
```

Hmm. That didn't work. Hmm

```bash
cassandra-stuff $ docker ps
CONTAINER ID   IMAGE       COMMAND                  CREATED         STATUS         PORTS                                         NAMES
9fc149b8dd0b   cassandra   "docker-entrypoint.s…"   5 minutes ago   Up 5 minutes   7000-7001/tcp, 7199/tcp, 9042/tcp, 9160/tcp   cassandra
```

```bash
cassandra-stuff $ docker network ls
NETWORK ID     NAME        DRIVER    SCOPE
d545ade582da   bridge      bridge    local
df8b9bc77595   cassandra   bridge    local
b58eb8dfc889   host        host      local
e56b3e3f8703   kind        bridge    local
e2aa207b7a1b   none        null      local
cassandra-stuff $ docker network 

Usage:  docker network COMMAND

Manage networks

Commands:
  connect     Connect a container to a network
  create      Create a network
  disconnect  Disconnect a container from a network
  inspect     Display detailed information on one or more networks
  ls          List networks
  prune       Remove all unused networks
  rm          Remove one or more networks

Run 'docker network COMMAND --help' for more information on a command.
cassandra-stuff $ docker network inspect cassandra
[
    {
        "Name": "cassandra",
        "Id": "df8b9bc775957ec1e1197dbe79bad189a127eba83de5589f15ff01c96e82c7f0",
        "Created": "2021-08-21T06:47:16.7675841Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.19.0.0/16",
                    "Gateway": "172.19.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "9fc149b8dd0ba7b88cf4283ef86d760ea46c2182d3050c3eb03c8c400d41d854": {
                "Name": "cassandra",
                "EndpointID": "e90b46e2b32b82e6061cd51be70fe721e0a97c8e6f43194bb1e0cc6b88a2bb23",
                "MacAddress": "02:42:ac:13:00:02",
                "IPv4Address": "172.19.0.2/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]
cassandra-stuff $ 
```

I'm wondering what went wrong, hmm.

Port 9042 looks okay, host too looks okay - `cassandra` which is the container name

https://hub.docker.com/r/nuvo/docker-cqlsh

In fact those are the defaults too, hmm

Oh. The transport version, I think we will have to use v4 ? I don't know. I don't know if Cassandra v4 has a change in "transport version" too. Currently the client uses v3.4.4 by default, hmm

https://hub.docker.com/_/cassandra

Gonna try a command like this from the cassandra docker image docs

```bash
$ docker run -it --network some-network --rm cassandra cqlsh some-cassandra
```

```bash
cassandra-stuff $ docker run -it --network cassandra --rm cassandra cqlsh cassandra
Connected to Test Cluster at cassandra:9042
[cqlsh 6.0.0 | Cassandra 4.0.0 | CQL spec 3.4.5 | Native protocol v5]
Use HELP for help.
cqlsh> \t
Invalid syntax at char 1
  \t
  ^
cqlsh> show
Improper show command.
cqlsh> show tables
Improper show command.
cqlsh> help

Documented shell commands:
===========================
CAPTURE  CLS          COPY  DESCRIBE  EXPAND  LOGIN   SERIAL  SOURCE   UNICODE
CLEAR    CONSISTENCY  DESC  EXIT      HELP    PAGING  SHOW    TRACING

CQL help topics:
================
AGGREGATES               CREATE_KEYSPACE           DROP_TRIGGER      TEXT     
ALTER_KEYSPACE           CREATE_MATERIALIZED_VIEW  DROP_TYPE         TIME     
ALTER_MATERIALIZED_VIEW  CREATE_ROLE               DROP_USER         TIMESTAMP
ALTER_TABLE              CREATE_TABLE              FUNCTIONS         TRUNCATE 
ALTER_TYPE               CREATE_TRIGGER            GRANT             TYPES    
ALTER_USER               CREATE_TYPE               INSERT            UPDATE   
APPLY                    CREATE_USER               INSERT_JSON       USE      
ASCII                    DATE                      INT               UUID     
BATCH                    DELETE                    JSON            
BEGIN                    DROP_AGGREGATE            KEYWORDS        
BLOB                     DROP_COLUMNFAMILY         LIST_PERMISSIONS
BOOLEAN                  DROP_FUNCTION             LIST_ROLES      
COUNTER                  DROP_INDEX                LIST_USERS      
CREATE_AGGREGATE         DROP_KEYSPACE             PERMISSIONS     
CREATE_COLUMNFAMILY      DROP_MATERIALIZED_VIEW    REVOKE          
CREATE_FUNCTION          DROP_ROLE                 SELECT          
CREATE_INDEX             DROP_TABLE                SELECT_JSON     

cqlsh> help show

        SHOW [cqlsh only]

          Displays information about the current cqlsh session. Can be called in
          the following ways:

        SHOW VERSION

          Shows the version and build of the connected Cassandra instance, as
          well as the version of the CQL spec that the connected Cassandra
          instance understands.

        SHOW HOST

          Shows where cqlsh is currently connected.

        SHOW SESSION <sessionid>

          Pretty-prints the requested tracing session.
        
cqlsh> show version
[cqlsh 6.0.0 | Cassandra 4.0.0 | CQL spec 3.4.5 | Native protocol v5]
cqlsh> show host
Connected to Test Cluster at cassandra:9042
cqlsh> show session
Improper show command.
cqlsh> show
Improper show command.
cqlsh> show csqlsh only
Improper show command.
cqlsh> tracing
Tracing is currently disabled. Use TRACING ON to enable.
cqlsh> tracing on
Now Tracing is enabled
cqlsh> tracing
Tracing is currently enabled. Use TRACING OFF to disable
cqlsh> show session
Improper show command.
cqlsh> show session 1
Improper show command.
cqlsh> show version 1
Improper show command.
cqlsh> show version
[cqlsh 6.0.0 | Cassandra 4.0.0 | CQL spec 3.4.5 | Native protocol v5]
cqlsh> 
cassandra-stuff $ docker run -it --network cassandra --rm cassandra cqlsh cassandra 
cassandra-stuff $ docker ps
CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS          PORTS                                         NAMES
9fc149b8dd0b   cassandra   "docker-entrypoint.s…"   14 minutes ago   Up 14 minutes   7000-7001/tcp, 7199/tcp, 9042/tcp, 9160/tcp   cassandra
cassandra-stuff $ docker ps -a
CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS          PORTS                                         NAMES
9fc149b8dd0b   cassandra   "docker-entrypoint.s…"   14 minutes ago   Up 14 minutes   7000-7001/tcp, 7199/tcp, 9042/tcp, 9160/tcp   cassandra
cassandra-stuff $ docker exec -it cassandra bash
root@cassandra:/# cql
bash: cql: command not found
root@cassandra:/# cqlsh
Connected to Test Cluster at 127.0.0.1:9042
[cqlsh 6.0.0 | Cassandra 4.0.0 | CQL spec 3.4.5 | Native protocol v5]
Use HELP for help.
cqlsh> 
root@cassandra:/# cqlsh
cqlsh     cqlsh.py  
root@cassandra:/# cqlsh
cqlsh     cqlsh.py  
root@cassandra:/# cas
case       cassandra  
root@cassandra:/# cas
case       cassandra  
root@cassandra:/# ls
bin   dev  home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  etc  lib   lib64  media   opt  root  sbin  sys  usr
root@cassandra:/# ls /etc/
adduser.conf            deluser.conf  hostname      libaudit.conf  networks       rc1.d        shells
alternatives            dpkg          hosts         locale.alias   nsswitch.conf  rc2.d        skel
apt                     e2scrub.conf  init.d        locale.gen     opt            rc3.d        ssl
bash.bashrc             environment   inputrc       localtime      os-release     rc4.d        subgid
bindresvport.blacklist  fonts         iproute2      login.defs     pam.conf       rc5.d        subuid
ca-certificates         fstab         issue         logrotate.d    pam.d          rc6.d        sysctl.conf
ca-certificates.conf    gai.conf      issue.net     lsb-release    passwd         rcS.d        sysctl.d
cassandra               group         kernel        machine-id     passwd-        resolv.conf  systemd
cron.d                  group-        ldap          mailcap        profile        rmt          terminfo
cron.daily              gshadow       ld.so.cache   mailcap.order  profile.d      security     timezone
debconf.conf            gshadow-      ld.so.conf    mime.types     python3        selinux      ucf.conf
debian_version          gss           ld.so.conf.d  mke2fs.conf    python3.8      shadow       update-motd.d
default                 host.conf     legal         mtab           rc0.d          shadow-      xattr.conf
root@cassandra:/# ls /etc/cassandra/
cassandra-env.sh                hotspot_compiler       logback-tools.xml
cassandra-jaas.config           jvm11-clients.options  logback.xml
cassandra-rackdc.properties     jvm11-server.options   metrics-reporter-config-sample.yaml
cassandra-topology.properties   jvm8-clients.options   README.txt
cassandra.yaml                  jvm8-server.options    triggers
commitlog_archiving.properties  jvm-clients.options
cqlshrc.sample                  jvm-server.options
root@cassandra:/# exit
cassandra-stuff $ docker cp exploring/data.cql cassandra:~
cassandra-stuff $ docker exec -it cassandra bash
root@cassandra:/# pwd
/
root@cassandra:/# cd
root@cassandra:~# pwd
/root
root@cassandra:~# ls
root@cassandra:~# whoami
root
root@cassandra:~# cd ~
root@cassandra:~# ls
root@cassandra:~# exit
cassandra-stuff $ docker cp exploring/data.cql cassandra:/root
cassandra-stuff $ docker exec -it cassandra bash
root@cassandra:/# cd
root@cassandra:~# ls
data.cql
root@cassandra:~# cqlsh < data.cql 
root@cassandra:~# cqlsh
Connected to Test Cluster at 127.0.0.1:9042
[cqlsh 6.0.0 | Cassandra 4.0.0 | CQL spec 3.4.5 | Native protocol v5]
Use HELP for help.
cqlsh> SELECT * FROM store.shopping_cart ;

 userid | item_count | last_update_timestamp
--------+------------+---------------------------------
   1234 |          5 | 2021-08-21 07:03:00.377000+0000
   9876 |          2 | 2021-08-21 07:03:00.373000+0000

(2 rows)
cqlsh> INSERT INTO store.shopping_cart (userid, item_count) VALUES ('4567', 20);
cqlsh> SELECT * FROM store.shopping_cart ;

 userid | item_count | last_update_timestamp
--------+------------+---------------------------------
   4567 |         20 |                            null
   1234 |          5 | 2021-08-21 07:03:00.377000+0000
   9876 |          2 | 2021-08-21 07:03:00.373000+0000

(3 rows)
cqlsh> 
root@cassandra:~# 
```

That worked pretty well!! :D

So, that was interesting. Protocol version was v5 looking at

`[cqlsh 6.0.0 | Cassandra 4.0.0 | CQL spec 3.4.5 | Native protocol v5]`

There's client version - `cqlsh`, I think it's short for Cassandra Query Language Shell, there's server version, which is v4.0.0 and then Cassandra Query Language Spec version which is v3.4.5 and then Native protocol version which is v5

I'm guessing Native protocol is the protocol used for communicating between clients and servers, and maybe even among servers. Something to checkout [TODO]

So, next steps are
- https://cassandra.apache.org/_/cassandra-basics.html
- Docs. https://cassandra.apache.org/doc/latest/. But they put a wrong link. https://cassandra.apache.org/_/quickstart.html#docs
- https://cassandra.apache.org/_/case-studies.html

I think there's a lot of improvement for Cassandra folks in terms of quick starts docs and website, hmm
