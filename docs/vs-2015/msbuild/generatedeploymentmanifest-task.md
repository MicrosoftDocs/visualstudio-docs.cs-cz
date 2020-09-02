---
title: Úloha GenerateDeploymentManifest – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
ms.assetid: 0734ebda-734d-49c4-9642-8d9d919d45fd
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6f0c13e5ea8778ca91c30383287aaad6e965bb65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149604"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vygeneruje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest nasazení. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Manifest nasazení popisuje nasazení aplikace definováním jedinečné identity pro nasazení, určením vlastností nasazení, jako je například instalace nebo online režim, určení nastavení aktualizace aplikace a umístění aktualizací a označení odpovídajícího [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikace.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry pro `GenerateDeploymentManifest` úlohu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AssemblyName`|Volitelný `String` parametr.<br /><br /> Určuje `Name` pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, název je odvozen z `EntryPoint` `InputManifest` parametrů nebo. Pokud se název nedá odvodit, úloha vyvolá chybu.|  
|`AssemblyVersion`|Volitelný `String` parametr.<br /><br /> Určuje `Version` pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, úloha použije hodnotu "1.0.0.0".|  
|`CreateDesktopShortcut`|Volitelný `Boolean` parametr.<br /><br /> Pokud má hodnotu true, vytvoří se na ploše během instalace aplikace ClickOnce ikona.|  
|`DeploymentUrl`|Volitelný `String` parametr.<br /><br /> Určuje umístění aktualizace pro aplikaci. Pokud tento parametr není zadán, není pro aplikaci definováno žádné umístění aktualizace. Pokud `UpdateEnabled` je však parametr, je `true` nutné zadat umístění aktualizace. Zadaná hodnota by měla být úplná adresa URL nebo cesta UNC.|  
|`Description`|Volitelný `String` parametr.<br /><br /> Určuje volitelný popis aplikace.|  
|`DisallowUrlActivation`|Volitelný `Boolean` parametr.<br /><br /> Určuje, zda má být aplikace spouštěna automaticky při otevření prostřednictvím adresy URL. Pokud je tento parametr `true` , aplikaci lze spustit pouze z nabídky Start. Výchozí hodnota tohoto parametru je `false` . Tento vstup platí pouze v případě, že `Install` hodnota parametru je `true` .|  
|`EntryPoint`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Označuje vstupní bod pro vygenerované sestavení manifestu. V případě [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu nasazení určuje tento vstup [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikace.<br /><br /> V nástroji [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] je potřeba, aby [úloha GenerateApplicationManifest –](../msbuild/generateapplicationmanifest-task.md) `EntryPoint` vygenerovala manifest aplikace. (Sestavení nebo nativní manifesty nevyžadují `EntryPoint` .) Tento požadavek se vynutil s chybou buildu: MSB3185: EntryPoint není pro manifest zadaný.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] nevydá tuto chybu, pokud není `EntryPoint` zadán parametr úlohy. Místo toho \<customHostSpecified> je značka vložena jako podřízená \<entryPoint> značka, například:<br /><br /> `<entryPoint xmlns="urn:schemas-`<br /><br /> `microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Můžete přidat závislosti knihoven DLL do manifestu aplikace pomocí následujících kroků:<br /><br /> 1. vyřešte odkazy na sestavení voláním metody <xref:Microsoft.Build.Tasks.ResolveAssemblyReference> .<br />2. předejte výstup předchozí úlohy a samotné sestavení do <xref:Microsoft.Build.Tasks.ResolveManifestFiles> .<br />3. předejte závislosti pomocí `Dependencies` parametru do <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> .|  
|`ErrorReportUrl`|Volitelné [řetězec] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->ukazatele.<br /><br /> Určuje adresu URL webové stránky, která se zobrazí v dialogových oknech během instalace ClickOnce.|  
|`InputManifest`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Označuje vstupní dokument XML, který bude sloužit jako základ pro generátor manifestu. To umožňuje, aby se strukturovaná data, jako jsou definice vlastních manifestů, projevila ve výstupním manifestu. Kořenový element v dokumentu XML musí být uzlem sestavení v oboru názvů asmv1.|  
|`Install`|Volitelný `Boolean` parametr.<br /><br /> Určuje, jestli je aplikace nainstalovaná aplikace nebo aplikace jenom v režimu online. Pokud je tento parametr `true` , aplikace bude nainstalována v nabídce Start uživatele a lze ji odebrat pomocí dialogového okna Přidat nebo odebrat programy. Pokud je tento parametr `false` , aplikace je určena pro online použití z webové stránky. Výchozí hodnota tohoto parametru je `true` .|  
|`MapFileExtensions`|Volitelný `Boolean` parametr.<br /><br /> Určuje, zda je použito mapování přípon názvu souboru. deploy. Pokud je tento parametr `true` , každý soubor programu je publikován s příponou názvu souboru. deploy. Tato možnost je užitečná pro zabezpečení webového serveru k omezení počtu přípon názvů souborů, které je potřeba odblokovat, aby se povolilo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení aplikace. Výchozí hodnota tohoto parametru je `false` .|  
|`MaxTargetPath`|Volitelný `String` parametr.<br /><br /> Určuje maximální povolenou délku cesty souboru v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení aplikace. Je-li tento parametr zadán, bude na základě tohoto limitu kontrolována délka každé cesty souboru v aplikaci. Všechny položky, které překračují limit, způsobí upozornění sestavení. Pokud tento vstup není zadán nebo je nula, žádná kontrola se neprovádí.|  
|`MinimumRequiredVersion`|Volitelný `String` parametr.<br /><br /> Určuje, jestli uživatel může aktualizaci přeskočit. Pokud má uživatel verzi, která je menší než minimální požadovaná verze, nebude mít možnost tuto aktualizaci přeskočit. Tento vstup platí pouze v případě, že hodnota `Install` parametru je `true` .|  
|`OutputManifest`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje název vygenerovaného výstupního souboru manifestu. Pokud tento parametr není zadán, název výstupního souboru je odvozen z identity generovaného manifestu.|  
|`Platform`|Volitelný `String` parametr.<br /><br /> Určuje cílovou platformu aplikace. Tento parametr může mít následující hodnoty:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Výchozí hodnota je `AnyCPU`.|  
|`Product`|Volitelný `String` parametr.<br /><br /> Určuje název aplikace. Pokud tento parametr není zadán, název je odvozen z identity generovaného manifestu. Tento název se používá pro název zástupce v nabídce Start a je součástí názvu, který se zobrazí v dialogovém okně Přidat nebo odebrat programy.|  
|`Publisher`|Volitelný `String` parametr.<br /><br /> Určuje vydavatele aplikace. Pokud tento parametr není zadán, je název odvozen od registrovaného uživatele nebo z identity generovaného manifestu. Tento název se používá pro název složky v nabídce Start a je součástí názvu, který se zobrazí v dialogovém okně Přidat nebo odebrat programy.|  
|`SuiteNamel`|Volitelný `String` parametr.<br /><br /> Určuje název složky v nabídce Start, kde se aplikace nachází po nasazení ClickOnce.|  
|`SupportUrl`|Volitelný `String` parametr.<br /><br /> Určuje odkaz, který se zobrazí v dialogovém okně Přidat nebo odebrat programy pro aplikaci. Zadaná hodnota by měla být úplná adresa URL nebo cesta UNC.|  
|`TargetCulture`|Volitelný `String` parametr.<br /><br /> Určuje jazykovou verzi aplikace a určuje `Language` pole identity sestavení pro generovaný manifest. Není-li tento parametr zadán, předpokládá se, že aplikace je invariantní jazykové verze.|  
|`TrustUrlParameters`|Volitelný `Boolean` parametr.<br /><br /> Určuje, zda mají být pro aplikaci k dispozici parametry řetězce dotazu adresy URL. Výchozí hodnota tohoto parametru je `false` , což znamená, že parametry nebudou k dispozici pro aplikaci.|  
|`UpdateEnabled`|Volitelný `Boolean` parametr.<br /><br /> Určuje, zda je aplikace povolena pro aktualizace. Výchozí hodnota tohoto parametru je `false` . Tento parametr platí pouze v případě, že hodnota `Install` parametru je `true` .|  
|`UpdateInterval`|Volitelný `Int32` parametr.<br /><br /> Určuje interval aktualizace pro aplikaci. Výchozí hodnota tohoto parametru je nula. Tento parametr platí pouze v případě, že hodnoty `Install` `UpdateEnabled` parametrů a jsou oba `true` .|  
|`UpdateMode`|Volitelný `String` parametr.<br /><br /> Určuje, zda mají být aktualizace zkontrolovány v popředí před spuštěním aplikace nebo na pozadí, jako je aplikace spuštěna. Tento parametr může mít následující hodnoty:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Výchozí hodnota tohoto parametru je `Background` . Tento parametr platí pouze v případě, že hodnoty `Install` `UpdateEnabled` parametrů a jsou oba `true` .|  
|`UpdateUnit`|Volitelný `String` parametr.<br /><br /> Určuje jednotky pro `UpdateInterval` parametr. Tento parametr může mít následující hodnoty:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Tento parametr platí pouze v případě, že hodnoty `Install` `UpdateEnabled` parametrů a jsou oba `true` .|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.GenerateManifestBase> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam parametrů třídy Task naleznete v tématu [základní třída Task](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [GenerateApplicationManifest – – úloha](../msbuild/generateapplicationmanifest-task.md)   
 [SignFile – – úloha](../msbuild/signfile-task.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
