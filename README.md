## 🧭 **Resumo: Configuração de Instância de Banco de Dados no Microsoft Azure**

### 1. **Acesso à Plataforma**

* Acesse o portal da Azure: [https://portal.azure.com](https://portal.azure.com)
* Tenha uma conta com permissões adequadas (Admin ou Contributor).
* Recomenda-se o uso do **Azure Free Account** para testes iniciais (conta gratuita com crédito por 30 dias).
* Também é possivel ver a documentação no [Azure Learn](https://learn.microsoft.com/pt-br/azure/azure-sql/managed-instance/instance-create-quickstart?view=azuresql&tabs=azure-portal).

---

### 2. **Escolha do Serviço de Banco de Dados**

Azure oferece diversas opções:

* **Azure SQL Database** – Banco relacional baseado em SQL Server.
* **Azure Database for MySQL** – Ideal para apps PHP ou WordPress.
* **Azure Database for PostgreSQL** – Alternativa para apps que usam PostgreSQL.
* **Cosmos DB** – Banco NoSQL, ideal para escalabilidade global e baixa latência.

> 💡 *Dica:* Para estudos, o [Azure SQL Database](https://azure.microsoft.com/en-us/products/azure-sql/database/?&ef_id=_k_EAIaIQobChMIpK3zt9uIjQMVXUVIAB12kRG-EAAYASAAEgLJI_D_BwE_k_&OCID=AIDcmmzmnb0182_SEM__k_EAIaIQobChMIpK3zt9uIjQMVXUVIAB12kRG-EAAYASAAEgLJI_D_BwE_k_&gad_source=1&gbraid=0AAAAADcJh_vIGIf9H7zFm6AJ-EH3Y9YK8&gclid=EAIaIQobChMIpK3zt9uIjQMVXUVIAB12kRG-EAAYASAAEgLJI_D_BwE) é o mais comum e possui suporte nativo no portal com boas opções gratuitas.

---

### 3. **Criação da Instância**

**Passo a passo básico (exemplo com Azure SQL Database):**

1. No portal Azure, vá em **"Criar um recurso" > "Databases" > "SQL Database"**.
2. Preencha os campos obrigatórios:

   * **Subscription**: Selecione sua assinatura.
   * **Resource Group**: Crie um novo ou escolha existente.
   * **Database name**: Nome do banco de dados.
   * **Server**: Crie um novo servidor lógico ou selecione existente.

     * Nome, região, login de admin e senha.
   * **Compute + Storage**: Escolha o nível de desempenho (recomenda-se *Basic* ou *DTU-free* para testes).
   * **Backup e Redundância**: Pode deixar como padrão (LRS - Local Redundant Storage).
3. Clique em **"Review + create"**, revise as configurações e clique em **"Create"**.

> 💡 *Dica:* Use **tags** para organizar recursos (ex: ambiente=teste, dono=seunome).

---

### 4. **Configuração de Firewall**

* Vá até a instância criada.
* Em **"Configurações" > "Firewalls e redes virtuais"**, adicione o IP da sua máquina local.
* Habilite acesso para serviços do Azure (opcional).

> ⚠️ *Atenção:* Sem essa configuração, não será possível conectar ao banco de dados de fora da Azure.

---

### 5. **Conexão ao Banco de Dados**

* Instale o SQL Server Management Studio (SSMS) ou use Azure Data Studio.
* Dados de conexão:

  * **Servidor**: `<nomedoservidor>.database.windows.net`
  * **Usuário** e **senha** definidos na criação.
* Teste de conexão com SSMS: Escolha autenticação SQL e conecte.

> 🔐 *Dica de segurança:* Evite usar conta admin em aplicações. Crie usuários com permissões limitadas.

---

### 6. **Monitoramento e Manutenção**

* Use **Azure Monitor** para acompanhar performance.
* Configure alertas (ex: uso de CPU acima de 80%).
* Configure backups automáticos (já vêm ativados por padrão em muitos planos).

> 📈 *Dica:* O painel **Query Performance Insight** ajuda a identificar gargalos em queries SQL.

---

## 📘 **Anotações Finais**

* Azure cobra por consumo (tempo + recursos). Apague instâncias após testes para evitar cobranças.
* Use **Resource Groups** para agrupar recursos relacionados e facilitar a gestão.
* Considere o uso de **Azure CLI** ou **ARM Templates** para automação de deploys em ambientes profissionais.
* Verifique os **níveis de SLA** se for utilizar em produção (ex: 99,99% para Azure SQL Database).
  

---
