---
title: Nástroj CreateExpInstance | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0f7f52f45023106d3e504258a538823c1c8fbb4
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500654"
---
# <a name="createexpinstance-utility"></a>Nástroj CreateExpInstance
Použití **CreateExpInstance** nástroj k vytvoření, obnovit nebo odstranit experimentální instanci sady Visual Studio. Experimentální instanci slouží k ladění a testování rozšíření sady Visual Studio beze změny základní produkt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
## <a name="parameters"></a>Parametry  
 **/ Vytvoření** vytvoří experimentální instanci aplikace.  
  
 **/ Reset**  
 Odstraní experimentální instanci a pak vytvoří nový.  
  
 **/ Clean**  
 Odstraní experimentální instanci aplikace.  
  
 **/ VSInstance**  
 Název adresáře, který obsahuje základní instance sady Visual Studio ke kopírování.  
  
 **/ RootSuffix**  
 Přípona pro připojení k názvu adresáře experimentální instanci aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Při práci na rozšíření sady Visual Studio, můžete stisknutím klávesy F5 spusťte výchozí experimentální instanci a nainstalujte aktuální rozšíření. Pokud je k dispozici žádná experimentální instance, vytvoří Visual Studio, pokud má výchozí nastavení.  
  
 Výchozí umístění experimentální instanci aplikace závisí na číslo verze sady Visual Studio. Například pro sadu Visual Studio 2015 je umístění *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*. Všechny soubory v umístění adresáře jsou považovány za součást této instance. Všechny další experimentální instance nebude načten pomocí sady Visual Studio, pokud název adresáře se změní na výchozí umístění.  
  
 Visual Studio nepřistupuje k systémovým registrem při otevření experimentální instanci aplikace. Tím se liší od předchozí verze sady Visual Studio, který používá experimentální verzi podregistr registru.  
  
 **CreateExpInstance** nahrazuje nástroj **VsRegEx** nástroj.  
  
 Následující příklad Resetuje výchozí experimentální instanci sady Visual Studio:  
  
 **/ Reset CreateExpInstance.exe /VSInstance = 14.0 /RootSuffix = Exp**  
  
## <a name="see-also"></a>Viz také:  
 [Balíčky VSPackage](../../extensibility/internals/vspackages.md)