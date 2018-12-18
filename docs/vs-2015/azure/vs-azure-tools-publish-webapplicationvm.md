---
title: Publikování WebApplicationVM | Dokumentace Microsoftu
description: Zjistěte, jak nasadit webovou aplikaci k virtuálnímu počítači. Tento skript vytvoří požadované prostředky ve vašem předplatném Azure, pokud ještě neexistují.
author: ghogen
manager: douge
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: c2383e6d7b14d801a391a725f0482736fb926cd1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003355"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (skript Windows PowerShellu)
Nasadí webovou aplikaci k virtuálnímu počítači. Skript vytvoří požadované prostředky ve vašem předplatném Azure, pokud ještě neexistují.

```
Publish-WebApplicationVM
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>Konfigurace
Cesta ke konfiguračnímu souboru JSON popisující podrobnosti o nasazení.

| Aliasy | žádná |
| --- | --- |
| Povinné? |true |
| Pozice |pojmenované |
| Výchozí hodnota |žádná |
| Přijmout kanálový vstup? |false |
| Přijímat zástupné znaky? |false |

### <a name="subscriptionname"></a>subscriptionName
Název předplatného Azure, ve kterém chcete vytvořit virtuální počítač.

| Aliasy | žádná |
| --- | --- |
| Povinné? |false |
| Pozice |pojmenované |
| Výchozí hodnota |Použije první předplatné v souboru odběru |
| Přijmout kanálový vstup? |false |
| Přijímat zástupné znaky? |false |

### <a name="webdeploypackage"></a>WebDeployPackage
Cesta k balíčku pro nasazení webu k publikování do virtuálního počítače. Tento balíček můžete vytvořit pomocí Průvodce publikováním webu v sadě Visual Studio. Zobrazit [postupy: vytvoření balíčku pro nasazení webu v sadě Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx).

| Aliasy | žádná |
| --- | --- |
| Povinné? |false |
| Pozice |pojmenované |
| Výchozí hodnota |žádná |
| Přijmout kanálový vstup? |false |
| Přijímat zástupné znaky? |false |

### <a name="allowuntrusted"></a>AllowUntrusted
Pokud je hodnota true, povolí používání certifikátů, které nejsou podepsané důvěryhodným kořenovou autoritou.

| Aliasy | žádná |
| --- | --- |
| Povinné? |false |
| Pozice |pojmenované |
| Výchozí hodnota |false |
| Přijmout kanálový vstup? |false |
| Přijímat zástupné znaky? |false |

### <a name="vmpassword"></a>VMPassword
Přihlašovací údaje účtu virtuálního počítače. Příklad: - VMPassword @{Name = "admin"; Heslo = "password"}

| Aliasy | žádná |
| --- | --- |
| Povinné? |false |
| Pozice |pojmenované |
| Výchozí hodnota |žádná |
| Přijmout kanálový vstup? |false |
| Přijímat zástupné znaky? |false |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Přihlašovací údaje pro databázi SQL v Azure. Příklad: - DatabaseServerPassword @{Name = "admin"; Heslo = "password"}

| Aliasy | žádná |
| --- | --- |
| Povinné? |false |
| Pozice |pojmenované |
| Výchozí hodnota |žádná |
| Přijmout kanálový vstup? |false |
| Přijímat zástupné znaky? |false |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Pokud je hodnota true, tisk zpráv ze skriptu do výstupního datového proudu.

| Aliasy | žádná |
| --- | --- |
| Povinné? |false |
| Pozice |pojmenované |
| Výchozí hodnota |false |
| Přijmout kanálový vstup? |false |
| Přijímat zástupné znaky? |false |

## <a name="remarks"></a>Poznámky
Úplné vysvětlení toho, jak použít skript k vytvoření vývojových a testovacích prostředí, najdete v části [pomocí skriptů Windows Powershellu k publikování do vývojových a testovacích prostředí](vs-azure-tools-publishing-using-powershell-scripts.md).

Konfigurační soubor JSON má podrobnosti o co se má nasadit. Obsahuje informace, které jste zadali při vytváření projektu, jako je například název, skupinu vztahů, image virtuálního pevného disku a velikost virtuálního počítače. Zahrnuje také koncových bodů na virtuálním počítači, databázi, kterou chcete zřídit, pokud existuje a web parametrů nasazení. Následující kód ukazuje příklad konfigurace souboru JSON:

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Můžete upravit konfigurační soubor JSON, chcete-li změnit, co je zřízený. Virtuální počítače a cloudové služby jsou povinné, ale databáze část je nepovinná.

