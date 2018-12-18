---
title: Prvky izolovaného prostředí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e567fc212b9981d925fc11e8e0ae48132b3b05bf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816811"
---
# <a name="elements-of-the-isolated-shell"></a>Prvky izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete upravit nastavení registru, nastavení za běhu a vstupní bod aplikace izolovaného prostředí aplikace a jeho .vsct, .pkgdef, and.pkgundef soubory.  
  
## <a name="registry-settings"></a>Nastavení registru  
 .pkgdef a .pkgundef souborů změnit nastavení registru pro aplikací izolovaného prostředí. Při spuštění aplikace, nastavení registru jsou definované v následujícím pořadí:  
  
 Při spuštění aplikace, nastavení registru jsou definované v následujícím pořadí:  
  
1.  Vytvoří se klíč registru pro aplikaci.  
  
2.  Registr se aktualizuje ze souboru .pkgdef aplikace tak, že definujete zadaného klíče a položky.  
  
3.  Pro každý balíček, který je součástí vaší aplikace se aktualizuje registr ze souboru .pkgdef tohoto balíčku. Každý balíček je definován v souboru .pkgdef aplikace $RootKey$ \Packages\\{*vsPackageGuid*} klíče pro balíček.  
  
4.  Registr se aktualizuje z AppEnvConfig.pkgdef a BaseConfig.pkgdef v *cestu instalace sady Visual Studio SDK*\Common7\IDE\ShellExtensions\Platform adresáře. Tyto soubory jsou součástí sady Visual Studio a také součástí Distribuovatelný balíček prostředí Visual Studio Shell (izolovaný režim).  
  
5.  Registr se aktualizuje ze souboru .pkgundef aplikace tak, že odeberete zadaného klíče a položky.  
  
## <a name="run-time-settings"></a>Nastavení za běhu  
 Když uživatel spustí aplikaci, která izolovaného prostředí, volá vstupní bod spuštění z prostředí sady Visual Studio. Nastavení aplikace jsou definovány při spuštění aplikace, následujícím způsobem:  
  
1. Prostředí sady Visual Studio kontroluje pro konkrétní klíče registru aplikace. Pokud je nastavení pro klíč zadaný ve volání na začátku vstupní bod, tato hodnota přepíše hodnotu v registru.  
  
2. Pokud bod registru ani položka parametr určuje hodnotu nastavení a potom je použita výchozí hodnota pro nastavení.  
  
   Když uživatel spustí aplikaci z příkazového řádku, všechny přepínače příkazového řádku jsou předány do prostředí nástroje Visual Studio, které je zpracovává stejným způsobem, který provede Devenv. Další informace o přepínačích Devenv najdete v tématu [přepínače příkazového řádku nástroje Devenv](../ide/reference/devenv-command-line-switches.md) a [přepínače příkazového řádku nástroje Devenv pro vývoj rozšíření VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Další informace o způsobu balíček zaregistruje přepínače příkazového řádku najdete v tématu [přidáním přepínače příkazového řádku](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Vstupní bod Start  
 Soubor Appenvstub.dll obsahuje vstupní body při přístupu k izolované prostředí. Při spuštění aplikace, které volá vstupní bod Appenvstub.dll Start.  
  
 Můžete změnit chování aplikace změnou hodnoty poslední parametr, který je předán vstupnímu bodu Start. Další informace najdete v tématu [izolovaného prostředí vstupní bod parametrů (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>Na. Soubor Vsct  
 Souboru .vsct umožňuje určit, jaké standardní prvky uživatelského rozhraní Visual Studio jsou k dispozici v aplikaci. Další informace najdete v tématu [. Soubory Vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>Na. Soubor Pkgundef  
 Když je aplikace nainstalována v počítači, na kterém je nainstalována aplikace Visual Studio, kopii položky registru sady Visual Studio se provede pro aplikaci. Ve výchozím nastavení aplikace používá rozšíření VSPackages, která jsou již nainstalovány v počítači. Souboru .pkgundef umožňuje vyloučit položky registru, aby bylo možné odebrat konkrétní prvky prostředí sady Visual Studio nebo rozšíření z aplikace. Další informace najdete v tématu [. Soubory Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Souboru .pkgundef umožňuje vyloučit položky registru, aby bylo možné odebrat konkrétní prvky prostředí sady Visual Studio nebo rozšíření z aplikace. Další informace najdete v tématu [. Soubory Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Sada balíček identifikátory GUID, které se můžete vyloučit jsou uvedeny v [balíček identifikátory GUID z funkce sady Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>Na. Soubor Pkgdef  
 Soubor .pkgdef umožňuje definovat položky registru pro aplikace, které se nastavují při instalaci aplikace. Popis souboru .pkgdef a seznam položky registru, které používá prostředí sady Visual Studio najdete v tématu [. Soubory Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Náhradní řetězce  
 Náhradní řetězce použité v souborech .pkgdef a .pkgundef jsou uvedeny v [náhradní řetězce použité v. Pkgdef a. Soubory Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Další nastavení  
 Pokud vaše aplikace izolovaného prostředí závisí Microsoft.VisualStudio.GraphModel.dll, budete muset přidat následující přesměrování vazby do souboru .config aplikace izolovaného prostředí:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```

