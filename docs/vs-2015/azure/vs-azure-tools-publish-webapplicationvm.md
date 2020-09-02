---
title: Publikovat – WebApplicationVM | Microsoft Docs
description: Přečtěte si, jak nasadit webovou aplikaci na virtuální počítač. Tento skript vytvoří požadované prostředky v předplatném Azure, pokud už neexistují.
author: ghogen
manager: jillfra
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: e35f5decee2a908a9d1075ff3f6365a1d358c7b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "70739312"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (skript Windows PowerShellu)
Nasadí webovou aplikaci na virtuální počítač. Skript vytvoří požadované prostředky v předplatném Azure, pokud už neexistují.

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
Cesta ke konfiguračnímu souboru JSON, který popisuje podrobnosti nasazení.

| Aliasy | žádné |
| --- | --- |
| Povinné? |true |
| Pozice |pojmenované |
| Výchozí hodnota |žádné |
| Přijmout vstup kanálu? |false (nepravda) |
| Přijmout zástupné znaky? |false (nepravda) |

### <a name="subscriptionname"></a>SubscriptionName
Název předplatného Azure, ve kterém chcete vytvořit virtuální počítač.

| Aliasy | žádné |
| --- | --- |
| Povinné? |false (nepravda) |
| Pozice |pojmenované |
| Výchozí hodnota |Používá první předplatné v souboru předplatného. |
| Přijmout vstup kanálu? |false (nepravda) |
| Přijmout zástupné znaky? |false (nepravda) |

### <a name="webdeploypackage"></a>WebDeployPackage
Cesta k balíčku pro nasazení webu, který se má publikovat na virtuálním počítači. Tento balíček můžete vytvořit pomocí Průvodce publikováním webu v aplikaci Visual Studio. Viz [Postupy: vytvoření balíčku pro nasazení webu v aplikaci Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx).

| Aliasy | žádné |
| --- | --- |
| Povinné? |false (nepravda) |
| Pozice |pojmenované |
| Výchozí hodnota |žádné |
| Přijmout vstup kanálu? |false (nepravda) |
| Přijmout zástupné znaky? |false (nepravda) |

### <a name="allowuntrusted"></a>AllowUntrusted
Pokud má hodnotu true, povolí použití certifikátů, které nejsou podepsané důvěryhodnou kořenovou autoritou.

| Aliasy | žádné |
| --- | --- |
| Povinné? |false (nepravda) |
| Pozice |pojmenované |
| Výchozí hodnota |false (nepravda) |
| Přijmout vstup kanálu? |false (nepravda) |
| Přijmout zástupné znaky? |false (nepravda) |

### <a name="vmpassword"></a>VMPassword
Přihlašovací údaje účtu virtuálního počítače Příklad:-VMPassword @ {Name = "admin"; Heslo = "heslo"}

| Aliasy | žádné |
| --- | --- |
| Povinné? |false (nepravda) |
| Pozice |pojmenované |
| Výchozí hodnota |žádné |
| Přijmout vstup kanálu? |false (nepravda) |
| Přijmout zástupné znaky? |false (nepravda) |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Přihlašovací údaje pro SQL Database v Azure Příklad:-DatabaseServerPassword @ {Name = "admin"; Heslo = "heslo"}

| Aliasy | žádné |
| --- | --- |
| Povinné? |false (nepravda) |
| Pozice |pojmenované |
| Výchozí hodnota |žádné |
| Přijmout vstup kanálu? |false (nepravda) |
| Přijmout zástupné znaky? |false (nepravda) |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Pokud je nastaveno na true, vytiskněte zprávy ze skriptu do výstupního datového proudu.

| Aliasy | žádné |
| --- | --- |
| Povinné? |false (nepravda) |
| Pozice |pojmenované |
| Výchozí hodnota |false (nepravda) |
| Přijmout vstup kanálu? |false (nepravda) |
| Přijmout zástupné znaky? |false (nepravda) |

## <a name="remarks"></a>Poznámky
Úplné vysvětlení způsobu použití skriptu k vytváření vývojových a testovacích prostředí najdete v tématu [použití skriptů prostředí Windows PowerShell pro publikování do vývojových a testovacích prostředí](vs-azure-tools-publishing-using-powershell-scripts.md).

Konfigurační soubor JSON určuje podrobnosti o tom, co má být nasazeno. Obsahuje informace, které jste zadali při vytváření projektu, jako je název, skupina vztahů, bitová kopie VHD a velikost virtuálního počítače. Zahrnuje taky koncové body na virtuálním počítači, databáze, které se mají zřídit, pokud existují, a parametry nasazení webu. Následující kód ukazuje příklad konfiguračního souboru JSON:

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

Úpravou konfiguračního souboru JSON můžete změnit, co je zřízené. Vyžaduje se virtuální počítač a cloudová služba, ale oddíl databáze je nepovinný.
