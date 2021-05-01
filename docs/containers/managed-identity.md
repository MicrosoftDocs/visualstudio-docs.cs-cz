---
title: Použití spravované identity s mostem na Kubernetes
ms.technology: vs-azure
ms.date: 04/28/2021
ms.topic: conceptual
description: Naučte se používat spravovanou identitu Azure Active Directory (Azure AD) v clusteru AKS s mostem na Kubernetes.
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: e4847b25531b48c8200a2620ca3e975f9677c881
ms.sourcegitcommit: 60b7a6159045a44293043a519c8ea6d915bf2c31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/01/2021
ms.locfileid: "108335087"
---
# <a name="use-managed-identity-with-bridge-to-kubernetes"></a>Použití spravované identity s mostem na Kubernetes

Pokud váš cluster AKS využívá [spravované](/azure/active-directory/managed-identities-azure-resources/overview) funkce zabezpečení identity k zabezpečení přístupu k tajným klíčům a prostředkům, most na Kubernetes potřebuje speciální konfiguraci, aby zajistil, že může s těmito funkcemi pracovat. Token Azure Active Directory (AD) je nutné stáhnout do místního počítače, aby bylo zajištěno, že je místní spouštění a ladění správně zabezpečeno a že vyžaduje speciální konfiguraci v Bridge do Kubernetes. Tento článek popisuje, jak nakonfigurovat most na Kubernetes, aby fungoval se službami, které používají spravovanou identitu.

## <a name="how-to-configure-your-service-to-use-managed-identity"></a>Jak nakonfigurovat službu tak, aby používala spravovanou identitu

Pokud chcete povolit místní počítač s podporou pro spravovanou identitu, v souboru *KubernetesLocalConfig. yaml* v `enableFeatures` části přidejte `ManagedIdentity` . Přidejte `enableFeatures` oddíl, pokud tam ještě není.

```yaml
enableFeatures:
    ManagedIdentity
```

> [!WARNING]
> Při práci s vývojovým clustery, ne v produkčních clusterech, se ujistěte, že používáte jenom spravovanou identitu pro most a Kubernetes, protože token Azure AD se načte do místního počítače, který představuje potenciální bezpečnostní riziko.

Pokud nemáte soubor *KubernetesLocalConfig. yaml* , můžete ho vytvořit. informace najdete v tématu [How to: Configure most to Kubernetes](configure-bridge-to-kubernetes.md).

## <a name="how-to-fetch-the-azure-active-directory-tokens"></a>Jak načíst tokeny Azure Active Directory

Při načítání tokenu je nutné zajistit, že se spoléháte na buď <xref:Azure.Identity.DefaultAzureCredential> nebo <xref:Azure.Identity.ManagedIdentityCredential> v kódu.

Následující kód jazyka C# ukazuje, jak načíst přihlašovací údaje účtu úložiště při použití `ManagedIdentityCredential` :

```csharp
var credential = new ManagedIdentityCredential(miClientId);
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Následující kód ukazuje, jak načíst přihlašovací údaje účtu úložiště při použití DefaultAzureCredential:

```csharp
var credential = new DefaultAzureCredential();
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Další informace o tom, jak získat přístup k dalším prostředkům Azure pomocí spravované identity, najdete v části [Další kroky](#next-steps) .

## <a name="receive-azure-alerts-when-tokens-are-downloaded"></a>Dostávat upozornění Azure při stažení tokenů

Kdykoli použijete pro Kubernetes ve službě most, token Azure AD se stáhne do místního počítače. Můžete povolit upozorňování Azure na výstrahy, když k ní dojde. Informace najdete v tématu [Povolení Azure Defenderu](/azure/security-center/enable-azure-defender). Počítejte s tím, že je účtován poplatek (po uplynutí 30denní zkušební doby).

## <a name="next-steps"></a>Další kroky

Teď, když jste nakonfigurovali most na Kubernetes, abyste mohli pracovat s clusterem AKS, který používá spravovanou identitu, můžete ladit jako normální. Viz [most-to-Kubernetes. MD # Connect-to-your-cluster-and-Debug-a-Service].

Další informace o použití spravované identifikace pro přístup k prostředkům Azure pomocí následujících kurzů:

- [Kurz: Použití spravované identity přiřazené systémem na virtuální počítači s Linuxem pro přístup k Azure Storage](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-storage)
- [Kurz: Použití spravované identity přiřazené systémem virtuálního počítače s Linuxem pro přístup k Azure Data Lake Storu](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-datalake)
- [Kurz: Použití spravované identity přiřazené systémem na virtuálním počítači s Linuxem pro přístup k Azure Key Vaultu](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-nonaad)

V této části najdete další kurzy i pro přístup k dalším prostředkům Azure pomocí spravované identity.

## <a name="see-also"></a>Viz také

[Azure Active Directory](/azure/active-directory/managed-identities-azure-resources/)
