---
title: Úloha GenerateDeploymentManifest | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca55f3eeb9b3119b27e67dcb0255f8386c521af6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634068"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest – úloha

Generuje manifest nasazení ClickOnce. Manifest nasazení ClickOnce popisuje nasazení aplikace definováním jedinečné identity pro nasazení, identifikací vlastností nasazení, jako je režim instalace nebo online, určením nastavení aktualizace aplikace a umístění aktualizací a označující odpovídající manifest aplikace ClickOnce.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `GenerateDeploymentManifest` úkolu.

| Parametr | Popis |
|--------------------------| - |
| `AssemblyName` | Volitelný `String` parametr.<br /><br /> Určuje `Name` pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, název je `EntryPoint` odvozen `InputManifest` z parametry nebo. Pokud název nelze odvodit, úloha vyvolá chybu. |
| `AssemblyVersion` | Volitelný `String` parametr.<br /><br /> Určuje `Version` pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, úkol použije hodnotu "1.0.0.0". |
| `CreateDesktopShortcut` | Volitelný `Boolean` parametr.<br /><br /> Pokud true, ikona je vytvořen na ploše během ClickOnce instalace aplikace. |
| `DeploymentUrl` | Volitelný `String` parametr.<br /><br /> Určuje umístění aktualizace aplikace. Pokud tento parametr není zadán, není pro aplikaci definováno žádné umístění aktualizace. Pokud je `true` `UpdateEnabled` však parametrem , musí být zadáno umístění aktualizace. Zadanou hodnotou by měla být plně kvalifikovaná adresa URL nebo cesta UNC. |
| `Description` | Volitelný `String` parametr.<br /><br /> Určuje volitelný popis aplikace. |
| `DisallowUrlActivation` | Volitelný `Boolean` parametr.<br /><br /> Určuje, zda má být aplikace spuštěna automaticky při otevření prostřednictvím adresy URL. Pokud je `true`tento parametr , aplikace může být spuštěna pouze z nabídky **Start.** Výchozí hodnota tohoto parametru je `false`. Tento vstup platí pouze `Install` v `true`případě, že je hodnota parametru . |
| `EntryPoint` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Označuje vstupní bod pro sestavení generovaného manifestu. Pro manifest nasazení ClickOnce tento vstup určuje manifest aplikace ClickOnce.<br /><br />Pokud `EntryPoint` není zadán parametr úkolu, `<customHostSpecified>` je značka vložena `<entryPoint>` jako podřízená značka značky, například:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Závislosti dll můžete přidat do manifestu aplikace pomocí následujících kroků:<br /><br /> 1. Vyřešte odkazy <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>na sestavení voláním .<br />2. Předají výstup předchozí úlohy <xref:Microsoft.Build.Tasks.ResolveManifestFiles>a samotné sestavení do .<br />3. Předajte závislosti `Dependencies` pomocí <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>parametru na . |
| `ErrorReportUrl` | Volitelný <xref:System.String?displayProperty=fullName> parametr.<br /><br /> Určuje adresu URL webové stránky, která je zobrazena v dialogových oknech během instalace ClickOnce. |
| `InputManifest` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Označuje vstupní dokument XML, který má sloužit jako základ pro generátor manifestu. To umožňuje strukturovaná data, jako jsou vlastní definice manifestu, které mají být zohledněny ve výstupním manifestu. Kořenový prvek v dokumentu XML musí být uzel sestavení v oboru názvů asmv1. |
| `Install` | Volitelný `Boolean` parametr.<br /><br /> Určuje, zda se jedná o nainstalovanou aplikaci nebo o aplikaci pouze online. Pokud je `true`tento parametr , aplikace bude nainstalována v nabídce **Start** uživatele a může být odebrána pomocí dialogového okna Přidat **nebo odebrat programy.** Pokud je `false`tento parametr , aplikace je určena pro online použití z webové stránky. Výchozí hodnota tohoto parametru je `true`. |
| `MapFileExtensions` | Volitelný `Boolean` parametr.<br /><br /> Určuje, zda bude použito mapování přípon *.deploy.* Pokud je `true`tento parametr , každý soubor programu je publikován s příponou *.deploy.* Tato možnost je užitečná pro zabezpečení webového serveru omezit počet přípon názvů souborů, které musí být odblokovány povolit ClickOnce nasazení aplikace. Výchozí hodnota tohoto parametru je `false`. |
| `MaxTargetPath` | Volitelný `String` parametr.<br /><br /> Určuje maximální povolenou délku cesty k souboru v nasazení aplikace ClickOnce. Pokud je tento parametr zadán, délka každé cesty k souboru v aplikaci je kontrolována proti tomuto limitu. Všechny položky, které překročí limit způsobí upozornění sestavení. Pokud tento vstup není zadán nebo je nula, není provedena žádná kontrola. |
| `MinimumRequiredVersion` | Volitelný `String` parametr.<br /><br /> Určuje, zda může uživatel aktualizaci přeskočit. Pokud má uživatel verzi, která je nižší než minimální požadované, nebude mít možnost přeskočit aktualizaci. Tento vstup platí pouze v `Install` případě, `true`že hodnota parametru je . |
| `OutputManifest` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje název generovaného výstupního souboru manifestu. Pokud tento parametr není zadán, název výstupního souboru je odvozen z identity generovaného manifestu. |
| `Platform` | Volitelný `String` parametr.<br /><br /> Určuje cílovou platformu aplikace. Tento parametr může mít následující hodnoty:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Výchozí hodnota je `AnyCPU`. |
| `Product` | Volitelný `String` parametr.<br /><br /> Určuje název aplikace. Pokud tento parametr není zadán, název je odvozen z identity generovaného manifestu. Tento název se používá pro název zástupce v nabídce **Start** a je součástí názvu, který se zobrazí v dialogovém okně **Přidat nebo odebrat programy.** |
| `Publisher` | Volitelný `String` parametr.<br /><br /> Určuje vydavatele aplikace. Pokud tento parametr není zadán, název je odvozen od registrovaného uživatele nebo identity generovaného manifestu. Tento název se používá pro název složky v nabídce **Start** a je součástí názvu, který se zobrazí v dialogovém okně **Přidat nebo odebrat programy.** |
| `SuiteNamel` | Volitelný `String` parametr.<br /><br /> Určuje název složky v nabídce **Start,** kde je aplikace umístěna po nasazení ClickOnce. |
| `SupportUrl` | Volitelný `String` parametr.<br /><br /> Určuje odkaz, který se zobrazí v dialogovém okně **Přidat nebo odebrat programy** pro aplikaci. Zadanou hodnotou by měla být plně kvalifikovaná adresa URL nebo cesta UNC. |
| `TargetCulture` | Volitelný `String` parametr.<br /><br /> Identifikuje jazykovou verzi aplikace a určuje `Language` pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, předpokládá se, že aplikace je invariantní jazykové verze. |
| `TrustUrlParameters` | Volitelný `Boolean` parametr.<br /><br /> Určuje, zda mají být aplikaci zpřístupněny parametry řetězce dotazu URL. Výchozí hodnota tohoto parametru je `false`, což znamená, že parametry nebudou k dispozici pro aplikaci. |
| `UpdateEnabled` | Volitelný `Boolean` parametr.<br /><br /> Označuje, zda je aplikace povolena pro aktualizace. Výchozí hodnota tohoto parametru je `false`. Tento parametr platí pouze v `Install` případě, `true`že hodnota parametru je . |
| `UpdateInterval` | Volitelný `Int32` parametr.<br /><br /> Určuje interval aktualizace aplikace. Výchozí hodnota tohoto parametru je nula. Tento parametr platí pouze v `Install` případě, že hodnoty a parametry `UpdateEnabled` jsou obě `true`. |
| `UpdateMode` | Volitelný `String` parametr.<br /><br /> Určuje, zda mají být aktualizace před spuštěním aplikace zkontrolovány v popředí nebo na pozadí při spuštění aplikace. Tento parametr může mít následující hodnoty:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Výchozí hodnota tohoto parametru je `Background`. Tento parametr platí pouze v `Install` případě, že hodnoty a parametry `UpdateEnabled` jsou obě `true`. |
| `UpdateUnit` | Volitelný `String` parametr.<br /><br /> Určuje jednotky parametru. `UpdateInterval` Tento parametr může mít následující hodnoty:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Tento parametr platí pouze v `Install` případě, že hodnoty a parametry `UpdateEnabled` jsou obě `true`. |

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.GenerateManifestBase> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam parametrů třídy Task naleznete v tématu [Základní třída úlohy](../msbuild/task-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Úloha GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)
- [Úloha SignFile](../msbuild/signfile-task.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
