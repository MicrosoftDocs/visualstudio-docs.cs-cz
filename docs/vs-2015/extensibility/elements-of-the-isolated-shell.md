---
title: Prvky izolovaného prostředí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204604"
---
# <a name="elements-of-the-isolated-shell"></a>Prvky izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete upravit nastavení registru, nastavení modulu runtime a vstupní bod aplikace vaší aplikace izolovaného prostředí a soubory. vsct,. pkgdef a. pkgundef.  
  
## <a name="registry-settings"></a>Nastavení registru  
 Soubory. pkgdef a. pkgundef upravují nastavení registru pro aplikaci izolovaného prostředí. Při spuštění aplikace jsou nastavení registru definována v následujícím pořadí:  
  
 Při spuštění aplikace jsou nastavení registru definována v následujícím pořadí:  
  
1. Vytvoří se klíč registru pro aplikaci.  
  
2. Registr se aktualizuje ze souboru. pkgdef aplikace tím, že definuje zadané klíče a položky.  
  
3. Pro každý balíček, který je součástí vaší aplikace, se registr aktualizuje ze souboru. pkgdef tohoto balíčku. Každý balíček je definován v souboru. pkgdef aplikace $RootKey pomocí klíče% \Packages \\ {*vsPackageGuid*} pro balíček.  
  
4. Registr se aktualizuje z AppEnvConfig. pkgdef a BaseConfig. pkgdef v adresáři pro *instalaci sady Visual Studio SDK*\Common7\IDE\ShellExtensions\Platform. Tyto soubory jsou součástí sady Visual Studio a také jsou součástí redistribuovatelného balíčku prostředí sady Visual Studio (izolovaný režim).  
  
5. Registr se aktualizuje ze souboru. pkgundef aplikace tím, že se odstraní zadané klíče a položky.  
  
## <a name="run-time-settings"></a>Nastavení běhu  
 Když uživatel spustí aplikaci izolovaného prostředí, zavolá počáteční vstupní bod prostředí sady Visual Studio. Nastavení aplikace jsou definována při spuštění aplikace následujícím způsobem:  
  
1. Prostředí sady Visual Studio kontroluje konkrétní klíče v registru aplikace. Pokud je nastavení pro klíč zadáno ve volání počátečního vstupního bodu, pak tato hodnota Přepisuje hodnotu v registru.  
  
2. Pokud ani položka registru ani parametr vstupního bodu neurčuje hodnotu nastavení, použije se výchozí hodnota pro toto nastavení.  
  
   Když uživatel spustí aplikaci z příkazového řádku, všechny přepínače příkazového řádku jsou předány do prostředí sady Visual Studio, které je zpracovává stejným způsobem jako devenv. Další informace o přepínačích devenv najdete v tématu přepínače [příkazového řádku devenv](../ide/reference/devenv-command-line-switches.md) a [přepínače příkazového řádku nástroje devenv pro vývoj pro VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Další informace o tom, jak balíček registruje pro přepínače příkazového řádku, najdete v tématu [přidání přepínačů příkazového řádku](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Počáteční vstupní bod  
 Soubor Appenvstub.dll obsahuje vstupní body pro přístup k izolovanému prostředí. Po spuštění aplikace zavolá počáteční vstupní bod Appenvstub.dll.  
  
 Chování aplikace můžete změnit tak, že změníte hodnotu posledního parametru, který je předán počátečnímu vstupnímu bodu. Další informace najdete v tématu [parametry vstupního bodu izolovaného prostředí (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>Okně. Soubor vsct  
 Soubor. vsct umožňuje určit, které standardní prvky uživatelského rozhraní sady Visual Studio jsou v aplikaci k dispozici. Další informace najdete v tématu [. Soubory vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>Okně. Soubor pkgundef  
 Pokud je aplikace nainstalována na počítači, ve kterém je již nainstalována aplikace Visual Studio, je vytvořena kopie položek registru sady Visual Studio pro aplikaci. Ve výchozím nastavení aplikace používá rozhraní VSPackage, která jsou již v počítači nainstalována. Soubor. pkgundef umožňuje vyloučit položky registru, aby bylo možné z aplikace odebrat konkrétní prvky prostředí nebo rozšíření sady Visual Studio. Další informace najdete v tématu [. Soubory pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Soubor. pkgundef umožňuje vyloučit položky registru, aby bylo možné z aplikace odebrat konkrétní prvky prostředí nebo rozšíření sady Visual Studio. Další informace najdete v tématu [. Soubory pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Sada identifikátorů GUID balíčků, které lze vyloučit, je uvedena v [části identifikátory GUID balíčků funkcí sady Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>Okně. Soubor pkgdef  
 Soubor. pkgdef umožňuje definovat položky registru pro aplikaci, která je nastavena při instalaci aplikace. Popis souboru. pkgdef a seznam položek registru, které používá prostředí sady Visual Studio, naleznete v tématu [. Soubory pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Náhradní řetězce  
 Náhradní řetězce použité v souborech. pkgdef a. pkgundef jsou uvedeny v části [náhradní řetězce používané v. Pkgdef a. Soubory pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Další nastavení  
 Pokud vaše aplikace izolovaného prostředí závisí na Microsoft.VisualStudio.GraphModel.dll, je nutné přidat následující přesměrování vazby do souboru. config aplikace izolovaného prostředí:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
