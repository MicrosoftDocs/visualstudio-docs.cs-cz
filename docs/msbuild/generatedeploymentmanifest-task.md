---
title: Generatedeploymentmanifest – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37ac7c6f1a840a38508e49ca15efdd08c2043da6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939641"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest – úloha

Generuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu nasazení. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu nasazení popisuje nasazení aplikace definicí jedinečné identity pro nasazení, identifikující vlastností nasazení, jako je například instalace nebo online režimu, určení aplikace aktualizací nastavení nebo umístění, a označením odpovídajícího [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikace.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `GenerateDeploymentManifest` úloh.


| Parametr | Popis |
|--------------------------| - |
| `AssemblyName` | Volitelné `String` parametru.<br /><br /> Určuje, `Name` pole identity sestavení pro generovaný manifest. Pokud tento parametr nezadáte, název je odvozen z `EntryPoint` nebo `InputManifest` parametry. Pokud název nelze odvodit, úloha vyvolá chybu. |
| `AssemblyVersion` | Volitelné `String` parametru.<br /><br /> Určuje, `Version` pole identity sestavení pro generovaný manifest. Pokud není tento parametr zadán, úkol používá hodnotu "1.0.0.0". |
| `CreateDesktopShortcut` | Volitelné `Boolean` parametru.<br /><br /> Při hodnotě true je vytvořena ikona na ploše během instalace aplikace ClickOnce. |
| `DeploymentUrl` | Volitelné `String` parametru.<br /><br /> Určuje umístění aktualizace pro aplikaci. Pokud není tento parametr zadán, je definován žádné umístění aktualizace pro aplikaci. Nicméně pokud `UpdateEnabled` parametr je `true`, umístění aktualizace musí být zadán. Zadaná hodnota musí být plně kvalifikovaná cesta URL nebo cestu UNC. |
| `Description` | Volitelné `String` parametru.<br /><br /> Určuje volitelný popis pro aplikaci. |
| `DisallowUrlActivation` | Volitelné `Boolean` parametru.<br /><br /> Určuje, zda aplikace spouštěna automaticky při otevření prostřednictvím adresy URL. Pokud je tento parametr `true`, aplikaci lze spustit pouze z **Start** nabídky. Výchozí hodnota tohoto parametru je `false`. Tento vstup platí pouze tehdy, když `Install` je hodnota parametru `true`. |
| `EntryPoint` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Označuje položku zadání pro generované sestavení manifestu. Pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest nasazení, tento vstup Určuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikace.<br /><br />Pokud `EntryPoint` není zadán parametr úlohy, `<customHostSpecified>` je vložena značka jako podřízený objekt `<entryPoint>` značku, například:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Závislosti mezi knihovnami DLL k manifestu aplikace můžete přidat pomocí následujících kroků:<br /><br /> 1.  Přeložit odkazy na sestavení pomocí volání <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>.<br />2.  Předejte výstup předchozího úkolu a samotného sestavení do <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3.  Předejte závislosti pomocí `Dependencies` parametr <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>. |
| `ErrorReportUrl` | Volitelné <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Určuje adresu URL webové stránky, který se zobrazí v dialogových oknech během instalace ClickOnce. |
| `InputManifest` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Označuje vstupní dokument XML, který bude sloužit jako základ pro generátor manifestu. To umožňuje strukturovaným datům, například definicím vlastního manifestu, se projevovat ve výstupním manifestu. Kořenový element v dokumentu XML musí být uzel sestavení v oboru názvů asmv1. |
| `Install` | Volitelné `Boolean` parametru.<br /><br /> Určuje, zda je aplikace nainstalovaná aplikace nebo aplikace pouze online. Pokud je tento parametr `true`, aplikace se nainstaluje na uživatele **Start** nabídky a můžete ji odstranit pomocí **přidat nebo odebrat programy** dialogové okno. Pokud je tento parametr `false`, aplikace je určena pro použití online z webové stránky. Výchozí hodnota tohoto parametru je `true`. |
| `MapFileExtensions` | Volitelné `Boolean` parametru.<br /><br /> Určuje, zda *.deploy* mapování přípon názvů souborů se používá. Pokud je tento parametr `true`, každý programový soubor je publikován s *.deploy* příponu názvu souboru. Tato možnost je užitečná pro zabezpečení webového serveru k omezení počtu přípon souborů, které musí být odblokovány pro povolení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení aplikace. Výchozí hodnota tohoto parametru je `false`. |
| `MaxTargetPath` | Volitelné `String` parametru.<br /><br /> Určuje maximální povolenou délku cesty souboru v [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení aplikace. Pokud tento parametr zadán, délka každé cesty souboru v aplikaci je porovnávána s tímto limitem. Všechny položky, které překračují limit, způsobí upozornění sestavení. Pokud tento vstup není zadán nebo je nula, žádná kontrola se neprovádí. |
| `MinimumRequiredVersion` | Volitelné `String` parametru.<br /><br /> Určuje, zda uživatel může přeskočit aktualizaci. Pokud má uživatel verzi, která je menší než požadované minimum, že nebude mít možnost Přeskočit aktualizaci. Tento vstup platí, jen když hodnoty `Install` parametr `true`. |
| `OutputManifest` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje název generovaného výstupního souboru manifestu. Pokud tento parametr nezadáte, název výstupního souboru je odvozen z identity generovaného manifestu. |
| `Platform` | Volitelné `String` parametru.<br /><br /> Určuje cílovou platformu aplikace. Tento parametr může mít následující hodnoty:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Výchozí hodnota je `AnyCPU`. |
| `Product` | Volitelné `String` parametru.<br /><br /> Určuje název aplikace. Pokud tento parametr nezadáte, název je odvozen z identity generovaného manifestu. Tento název se používá pro název zástupce na **Start** nabídce a je součástí názvu, který se zobrazí **přidat nebo odebrat programy** dialogové okno. |
| `Publisher` | Volitelné `String` parametru.<br /><br /> Určuje název vydavatele aplikace. Pokud tento parametr nezadáte, název je odvozen z registrovaného uživatele, nebo z identity generovaného manifestu. Tento název se používá pro název složky na **Start** nabídce a je součástí názvu, který se zobrazí **přidat nebo odebrat programy** dialogové okno. |
| `SuiteNamel` | Volitelné `String` parametru.<br /><br /> Určuje název složky **Start** nabídky kde je umístěna aplikace po nasazení ClickOnce. |
| `SupportUrl` | Volitelné `String` parametru.<br /><br /> Určuje, který se zobrazí odkaz **přidat nebo odebrat programy** dialogové okno pro aplikaci. Zadaná hodnota musí být plně kvalifikovaná cesta URL nebo cestu UNC. |
| `TargetCulture` | Volitelné `String` parametru.<br /><br /> Určuje jazykovou verzi aplikace a určuje, `Language` pole identity sestavení pro generovaný manifest. Pokud není tento parametr zadán, předpokládá se, že aplikace je invariantní jazyková verze. |
| `TrustUrlParameters` | Volitelné `Boolean` parametru.<br /><br /> Určuje, zda parametry řetězce dotazu adresy URL by měly k dispozici pro aplikaci. Výchozí hodnota tohoto parametru je `false`, což znamená, že parametry nebudou k dispozici pro aplikaci. |
| `UpdateEnabled` | Volitelné `Boolean` parametru.<br /><br /> Určuje, zda je aplikace povolena pro aktualizace. Výchozí hodnota tohoto parametru je `false`. Tento parametr platí, jen když hodnoty `Install` parametr `true`. |
| `UpdateInterval` | Volitelné `Int32` parametru.<br /><br /> Určuje interval aktualizace pro aplikaci. Výchozí hodnota tohoto parametru je nula. Tento parametr platí, jen když hodnoty `Install` a `UpdateEnabled` parametry jsou obě `true`. |
| `UpdateMode` | Volitelné `String` parametru.<br /><br /> Určuje, zda mají být aktualizace zkontrolovány na popředí před aplikace je spuštěná, nebo v pozadí, když aplikace běží. Tento parametr může mít následující hodnoty:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Výchozí hodnota tohoto parametru je `Background`. Tento parametr platí, jen když hodnoty `Install` a `UpdateEnabled` parametry jsou obě `true`. |
| `UpdateUnit` | Volitelné `String` parametru.<br /><br /> Určuje jednotky pro `UpdateInterval` parametru. Tento parametr může mít následující hodnoty:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Tento parametr platí, jen když hodnoty `Install` a `UpdateEnabled` parametry jsou obě `true`. |

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.GenerateManifestBase> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam parametrů třídy úkoly naleznete v tématu [Task – základní třída](../msbuild/task-base-class.md).

## <a name="see-also"></a>Viz také:

[Úlohy](../msbuild/msbuild-tasks.md)  
[Generateapplicationmanifest – úloha](../msbuild/generateapplicationmanifest-task.md)  
[Signfile – úloha](../msbuild/signfile-task.md)  
[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)