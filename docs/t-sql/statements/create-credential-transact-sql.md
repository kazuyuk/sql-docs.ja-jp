---
title: CREATE CREDENTIAL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREDENTIAL_TSQL
- SQL13.SWB.CREDENTIAL.GENERAL.F1
- CREATE CREDENTIAL
- CREATE_CREDENTIAL_TSQL
- CREDENTIAL
dev_langs:
- TSQL
helpviewer_keywords:
- SECRET clause
- authentication [SQL Server], credentials
- CREATE CREDENTIAL statement
- credentials [SQL Server], CREATE CREDENTIAL statement
ms.assetid: d5e9ae69-41d9-4e46-b13d-404b88a32d9d
caps.latest.revision: 51
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 87759a536e979600e7ff12d8ad932c4fcf4cd248
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39458076"
---
# <a name="create-credential-transact-sql"></a>CREATE CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  サーバー レベルの資格情報を作成します。 資格情報は、SQL Server 外部のリソースへの接続に必要な認証情報を含むレコードです。 通常、資格情報には Windows ユーザーとパスワードが含まれます。 たとえば、どこかにデータベースのバックアップを保存するには、その場所にアクセスするための特別な資格情報を SQL Server で提供することが必要な場合があります。 詳しくは、「[資格情報 (データベース エンジン)](../../relational-databases/security/authentication-access/credentials-database-engine.md)」をご覧ください。

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

> [!NOTE]  
>  データベース レベルで資格情報を作成するには、[CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md) を使います。 サーバーの複数のデータベースで同じ資格情報を使う必要がある場合は、サーバー レベルの資格情報を使います。 データベースの移植性を高めるには、データベース スコープの資格情報を使います。 新しいサーバーにデータベースを移動するとき、データベース スコープの資格情報はそれと共に移動します。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ではデータベース スコープの資格情報を使います。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE CREDENTIAL credential_name   
WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
        [ FOR CRYPTOGRAPHIC PROVIDER cryptographic_provider_name ]  
```  
  
## <a name="arguments"></a>引数  
 *credential_name*  
 作成する資格情報の名前を指定します。 *credential_name* はシャープ (#) 記号で始めることはできません。 ## で始まる資格情報はシステム資格情報です。  共有アクセス署名 (SAS) を使用する場合、この名前は、コンテナーのパスを一致する必要があります https で起動し、スラッシュを含めることはできません。 D は次の例を参照してください。  
  
 IDENTITY **='***identity_name***'**  
 サーバーの外部に接続するときに使用するアカウントの名前を指定します。 Azure Key Vault へのアクセスに資格情報を使うときは、**IDENTITY** はキー コンテナーの名前です。 後半の例 C を参照してください。 資格情報で Shared Access Signature (SAS) を使っているときは、**IDENTITY** は *SHARED ACCESS SIGNATURE* です。 D は次の例を参照してください。  
  
 SECRET **='***secret***'**  
 送信の認証に必要なシークレットを指定します。  
  
 Azure Key Vault へのアクセスに資格情報を使うときは、**CREATE CREDENTIAL** の **SECRET** 引数に、Azure Active Directory の**サービス プリンシパル**の \<*クライアント ID*> (ハイフンなし) と \<*シークレット*> を間のスペースなしで渡す必要があります。 後半の例 C を参照してください。 資格情報が Shared Access Signature を使っている場合は、**SECRET** は Shared Access Signature トークンです。 D は次の例を参照してください。  Azure コンテナーで格納済みアクセス ポリシーと Shared Access Signature を作成する方法について詳しくは、「[レッスン 1: Azure コンテナーに格納済みアクセス ポリシーと Shared Access Signature を作成する](../../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)」をご覧ください。  
  
 FOR CRYPTOGRAPHIC PROVIDER *cryptographic_provider_name*  
 "*拡張キー管理プロバイダー (EKM)*" の名前を指定します。 キーの管理について詳しくは、「[拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)」をご覧ください。  
  
## <a name="remarks"></a>Remarks  

 IDENTITY が Windows ユーザーの場合、このシークレットにはパスワードを指定できます。 シークレットはサービス マスター キーを使用して暗号化されます。 サービス マスター キーが再生成された場合、シークレットは新しいサービス マスター キーを使用して再度暗号化されます。  
  
 資格情報を作成した後、[CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) または [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) を使って、この資格情報を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにマップすることができます。 1 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインは 1 つの資格情報だけにマップできますが、1 つの資格情報は複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにマップできます。 詳しくは、「[資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)」をご覧ください。 サーバー レベルの資格情報は、ログインにのみマップでき、データベース ユーザーにはマップできません。 
  
 資格情報に関する情報は、[sys.credentials](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md) カタログ ビューで確認できます。  
  
 ログインにマップされたプロバイダーの資格情報がない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントにマップされた資格情報が使用されます。  
  
 それぞれが異なるプロバイダーで使用される資格情報であれば、1 つのログインに複数の資格情報をマップできます。 マップされた資格情報は、各ログインで各プロバイダーにつき 1 つだけ存在する必要があります。 同じ資格情報を他のログインにマップすることはできます。  
  
## <a name="permissions"></a>アクセス許可  
 **ALTER ANY CREDENTIAL** 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-basic-example"></a>A. 基本の例  
 次の例では、資格情報 `AlterEgo` を作成します。 この資格情報には Windows ユーザー `Mary5` とパスワードが含まれます。  
  
```  
CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
    SECRET = '<EnterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-credential-for-ekm"></a>B. EKM の資格情報の作成  
 次の例では、以前に EKM 管理ツールを使って EKM モジュール上に作成した `User1OnEKM` というアカウントを、基本的なアカウントの種類とパスワードと共に使用します。 サーバーの **sysadmin** アカウントで、EKM アカウントへの接続に使用する資格情報を作成し、`User1` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントに割り当てます。  
  
```  
CREATE CREDENTIAL CredentialForEKM  
    WITH IDENTITY='User1OnEKM', SECRET='<EnterStrongPasswordHere>'  
    FOR CRYPTOGRAPHIC PROVIDER MyEKMProvider;  
GO  
  
/* Modify the login to assign the cryptographic provider credential */  
ALTER LOGIN Login1  
ADD CREDENTIAL CredentialForEKM;  
  
/* Modify the login to assign a non cryptographic provider credential */   
ALTER LOGIN Login1  
WITH CREDENTIAL = AlterEgo;  
GO  
```  
  
### <a name="c-creating-a-credential-for-ekm-using-the-azure-key-vault"></a>C. Azure のキー コンテナーを使用して EKM の資格情報の作成  
 次の例では、**SQL Server コネクタ for Microsoft Azure Key Vault** を使って Azure Key Vault にアクセスするときに使う、[!INCLUDE[ssDE](../../includes/ssde-md.md)]用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資格情報を作成します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コネクタの完全な使用例については、「[Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)」をご覧ください。  
  
> [!IMPORTANT]  
>  **CREATE CREDENTIAL** の **IDENTITY** 引数には、資格情報コンテナー名が必要です。 **CREATE CREDENTIAL** の **SECRET** 引数には、\<*クライアント ID*> (ハイフンなし) と \<*シークレット*> を、間にスペースを入れずに一緒に渡す必要があります。  
  
 次の例で、 **クライアント ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) はハイフンを削除した文字列 `EF5C8E094D2A4A769998D93440D8115D` として入力し、 **シークレット** は文字列 *SECRET_DBEngine*として入力しています。  
  
```  
USE master;  
CREATE CREDENTIAL Azure_EKM_TDE_cred   
    WITH IDENTITY = 'ContosoKeyVault',   
    SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine'   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
```  
  
 次の例では、**クライアント ID** と**シークレット**の文字列に変数を使って、同じ資格情報を作成します。これらの文字列は連結されて **SECRET** 引数を形成します。 **REPLACE** 関数は、クライアント ID からハイフンを取り除く目的で使用されています。  
  
```  
DECLARE @AuthClientId uniqueidentifier = 'EF5C8E09-4D2A-4A76-9998-D93440D8115D';  
DECLARE @AuthClientSecret varchar(200) = 'SECRET_DBEngine';  
DECLARE @pwd varchar(max) = REPLACE(CONVERT(varchar(36), @AuthClientId) , '-', '') + @AuthClientSecret;  
  
EXEC ('CREATE CREDENTIAL Azure_EKM_TDE_cred   
    WITH IDENTITY = 'ContosoKeyVault', SECRET = ''' + @PWD + '''   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;');  
```  
  
### <a name="d-creating-a-credential-using-a-sas-token"></a>D. SAS トークンを使用して資格情報の作成  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで。  
  
 次の例では、SAS トークンを使用して共有アクセス署名資格情報を作成します。  Azure コンテナーで格納済みアクセス ポリシーと Shared Access Signature を作成してから、Shared Access Signature を使って資格情報を作成するチュートリアルについては、「[Tutorial: Using the Microsoft Azure Blob storage service with SQL Server 2016 databases](../../relational-databases/tutorial-use-azure-blob-storage-service-with-sql-server-2016.md)」(チュートリアル: Microsoft Azure BLOB ストレージ サービスと SQL Server 2016 データベースの使用) をご覧ください。  
  
> [!IMPORTANT]  
>  **CREDENTIAL NAME** 引数では、名前がコンテナーのパス (https で始まり、末尾のスラッシュを含まないもの) と一致する必要があります。 **IDENTITY** 引数には、名前 *SHARED ACCESS SIGNATURE* が必要です。 **SECRET** 引数には、Shared Access Signature トークンが必要です。  
  
```  
USE master  
CREATE CREDENTIAL [https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>] -- this name must match the container path, start with https and must not contain a trailing forward slash.  
   WITH IDENTITY='SHARED ACCESS SIGNATURE' -- this is a mandatory string and do not change it.   
   , SECRET = 'sharedaccesssignature' –- this is the shared access signature token   
GO    
```  
  
## <a name="see-also"></a>参照  
 [資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [ALTER CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-credential-transact-sql.md)   
 [DROP CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-credential-transact-sql.md)   
 [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [レッスン 2: Shared Access Signature を使用して SQL Server 資格情報を作成する](../../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)   
 [Shared Access Signatures](https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/)  
  
  
