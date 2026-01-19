# lab10
Got it 👍
Here is **Program-10** rewritten **clearly and exactly**, based on the photos you uploaded.
👉 **No `< >` anywhere**.
👉 Commands are **copy-paste ready**.

---

# ✅ **Program-10: Kubernetes Dashboard & CLI Monitoring (Minikube)**

---

## **Step 1: Start Minikube with CPU & Memory**

```bash
minikube start --cpus=2 --memory=4096
```

---

## **Step 2: Open Kubernetes Dashboard**

```bash
minikube dashboard
```

✔ Dashboard opens automatically in browser.

---

## **Step 3: Create `deployment.yaml`**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

---

## **Step 4: Create `service.yaml`**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: NodePort
```

---

## **Step 5: Apply Resources**

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

---

## **Step 6: Monitor via CLI**

```bash
kubectl get pods
```

---

## **Step 7: Check Nodes**

```bash
kubectl get nodes
```

---

## **Step 8: Check Services**

```bash
kubectl get svc
```

---

## **Step 9: Check Pod Logs**

First get pod name:

```bash
kubectl get pods
```

Then:

```bash
kubectl logs nginx-deployment-xxxxxxxxxx-yyyyy
```

(replace with **actual pod name**, no `< >`)

---

## **Step 10: Describe Pod**

```bash
kubectl describe pod nginx-deployment-xxxxxxxxxx-yyyyy
```

---

## **Step 11: Access Application**

```bash
minikube service nginx-service
```

✔ NGINX page opens in browser.

---

## **Step 12: Open Dashboard Again (optional)**

```bash
minikube dashboard
```

---

## **Step 13: Clean-up**

```bash
kubectl delete pods --all
kubectl delete svc --all
kubectl delete deployments --all
```

---

## 🧠 **Exam Rule (VERY IMPORTANT)**

❌ Never write `<pod-name>`
❌ Never write `<service-name>`

✅ Always use **real names shown by `kubectl get pods`**

---

If you want, I can now give you:

* 🔹 **Very short exam answer**
* 🔹 **Viva questions & answers**
* 🔹 **Only commands list (1 page)**
