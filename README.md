set up:
hostname -I
ping <>

server
python3 server.py --listen-ip 0.0.0.0 --listen-port 5000

client:
python3 client.py --target-ip 192.168.0.52 --target-port 4000 --timeout 2.0 --max-retries 5

proxy:
Test 1 — 0% drop, 0% delay
python3 proxy.py \
  --listen-ip 0.0.0.0 \
  --listen-port 4000 \
  --target-ip 192.168.0.53 \
  --target-port 5000 \
  --client-drop 0 \
  --server-drop 0 \
  --client-delay 0 \
  --server-delay 0 \
  --client-delay-time-min 0 \
  --client-delay-time-max 0 \
  --server-delay-time-min 0 \
  --server-delay-time-max 0


Test 2 — 50% drop, 0% delay
python3 proxy.py \
  --listen-ip 0.0.0.0 \
  --listen-port 4000 \
  --target-ip 192.168.0.53 \
  --target-port 5000 \
  --client-drop 50 \
  --server-drop 50 \
  --client-delay 0 \
  --server-delay 0 \
  --client-delay-time-min 0 \
  --client-delay-time-max 0 \
  --server-delay-time-min 0 \
  --server-delay-time-max 0

Test 3 — 100% drop, 0% delay
python3 proxy.py \
  --listen-ip 0.0.0.0 \
  --listen-port 4000 \
  --target-ip 192.168.0.53 \
  --target-port 5000 \
  --client-drop 100 \
  --server-drop 100 \
  --client-delay 0 \
  --server-delay 0 \
  --client-delay-time-min 0 \
  --client-delay-time-max 0 \
  --server-delay-time-min 0 \
  --server-delay-time-max 0

Test 4 — 0% drop, 50% delay, 100–500 ms
python3 proxy.py \
  --listen-ip 0.0.0.0 \
  --listen-port 4000 \
  --target-ip 192.168.0.53 \
  --target-port 5000 \
  --client-drop 0 \
  --server-drop 0 \
  --client-delay 50 \
  --server-delay 50 \
  --client-delay-time-min 100 \
  --client-delay-time-max 500 \
  --server-delay-time-min 100 \
  --server-delay-time-max 500

Test 5 — 0% drop, 100% delay, delay >= client timeout
python3 proxy.py \
  --listen-ip 0.0.0.0 \
  --listen-port 4000 \
  --target-ip 192.168.0.53 \
  --target-port 5000 \
  --client-drop 0 \
  --server-drop 0 \
  --client-delay 100 \
  --server-delay 100 \
  --client-delay-time-min 2500 \
  --client-delay-time-max 2500 \
  --server-delay-time-min 2500 \
  --server-delay-time-max 2500

Test 6 — 50% drop, 50% delay, delay >= client timeout
python3 proxy.py \
  --listen-ip 0.0.0.0 \
  --listen-port 4000 \
  --target-ip 192.168.0.53 \
  --target-port 5000 \
  --client-drop 50 \
  --server-drop 50 \
  --client-delay 50 \
  --server-delay 50 \
  --client-delay-time-min 2500 \
  --client-delay-time-max 2500 \
  --server-delay-time-min 2500 \
  --server-delay-time-max 2500
