# 🌐 Static Website on AWS with Terraform

Este projeto provisiona uma infraestrutura completa na AWS para hospedar um site estático utilizando:

- Amazon S3 (armazenamento de arquivos HTML/CSS/JS)
- CloudFront (CDN com HTTPS)
- ACM (certificado SSL)
- Route 53 (registro e DNS do domínio)
- Terraform (Infraestrutura como Código)

---

## 📦 Estrutura do Projeto

```
.
├── .github/workflows/deploy.yml    # GitHub Actions para deploy automático no S3
├── modules/                        # Módulos reutilizáveis (S3, ACM, CloudFront)
├── site/                           # Arquivos do site (index.html, etc.)
├── main.tf                         # Arquivos principais Terraform
├── variables.tf
├── terraform.tfvars
├── outputs.tf
└── README.md
```

---

## 🚀 Como usar

### 1. Requisitos

- Conta na AWS
- Usuário com permissão `AdministratorAccess` (ou equivalente)
- Terraform instalado (`>= 1.3`)
- AWS CLI configurado com `aws configure`
- Domínio registrado no Route 53

---

### 2. Provisionar a Infraestrutura

```bash
terraform init
terraform plan
terraform apply
```

> Isso irá criar:
> - Bucket S3
> - CloudFront com HTTPS
> - Validação de domínio via DNS
> - Certificado SSL no ACM
> - Registro DNS no Route 53

---

### 3. Deploy do site

#### Manual:

```bash
aws s3 cp site/index.html s3://andresantos.click/index.html
```

#### Automático via GitHub Actions:

A cada novo `git push` na branch `main`, o conteúdo da pasta `site/` será sincronizado com o bucket S3.

✅ Basta atualizar o HTML e dar `git push`.

---

## 🔐 Secrets para o GitHub Actions

Adicione dois segredos no repositório (em `Settings → Secrets and variables → Actions`):

| Nome                    | Valor                          |
|-------------------------|--------------------------------|
| `AWS_ACCESS_KEY_ID`     | Chave de acesso do usuário AWS |
| `AWS_SECRET_ACCESS_KEY` | Chave secreta do usuário AWS   |

---

## 💡 Possíveis melhorias

- Deploy com CI/CD mais robusto (ex: usar GitHub Actions + Terraform Cloud)
- Monitoramento com AWS CloudWatch
- Integração com domínio customizado via Route 53

---

## 📎 Link do site

➡️ [https://andresantos.click](https://andresantos.click)

---

## 🧑‍💻 Autor

**André Santos**  
Especialista em Infraestrutura | DevOps | Cloud | SRE  
🔗 [linkedin.com/in/andropovbr](https://www.linkedin.com/in/andropovbr)
