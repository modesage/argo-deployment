## STEPS:

1. create k8s cluster
2. install argocd
3. create github ops repo 
4. start argocd ui locally (port-forward)
5. initial username = admin, password = take from secret
6. create a new app in argocd for backend

- kind create --config ./clusters.yml --name local
- kubectl create namespace argocd
- kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
- kubectl port-forward svc/argocd-server -n argocd 8080:443
- kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode

# 🔹 Base64 Encoding and Decoding

## 🔹 **PowerShell (Windows)**

### Encode a String to Base64

```powershell
[Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes("postgres://username:password@host:port/database"))
```

### Decode a Base64 String to Plain Text

```powershell
[Text.Encoding]::UTF8.GetString([Convert]::FromBase64String("cG9zdGdyZXM6Ly91c2VybmFtZTpwYXNzd29yZEBob3N0OnBvcnQvZGF0YWJhc2U="))
```

---

### Encode a File to Base64

```powershell
[Convert]::ToBase64String([IO.File]::ReadAllBytes("C:\path\to\file.txt"))
```

### Decode a Base64 File to Original

```powershell
$base64 = Get-Content "C:\path\to\encoded.txt" -Raw
[IO.File]::WriteAllBytes("C:\path\to\decoded.txt", [Convert]::FromBase64String($base64))
```

---

## 🔹 **Linux (Bash)**

### Encode a String to Base64

```bash
echo -n "postgres://username:password@host:port/database" | base64
```

### Decode a Base64 String to Plain Text

```bash
echo -n "cG9zdGdyZXM6Ly91c2VybmFtZTpwYXNzd29yZEBob3N0OnBvcnQvZGF0YWJhc2U=" | base64 --decode
```

---

###  Encode a File to Base64

```bash
base64 file.txt > encoded.txt
```

### Decode a Base64 File to Original

```bash
base64 --decode encoded.txt > decoded.txt
```
