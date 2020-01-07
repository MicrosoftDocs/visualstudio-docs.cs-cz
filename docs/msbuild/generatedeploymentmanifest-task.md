---
title: Úloha GenerateDeploymentManifest – | Microsoft Docs
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
ms.openlocfilehash: fc953298241ec7c48bbf5ea87c902aa28b349ce0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588301"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest – úloha

Vygeneruje manifest nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Manifest nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] popisuje nasazení aplikace definováním jedinečné identity pro nasazení, určením vlastností nasazení, jako je například instalace nebo online režim, určení nastavení aktualizace aplikace a umístění aktualizací a označení odpovídajícího manifestu aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry pro úlohu `GenerateDeploymentManifest`.

| Parametr | Popis |
|--------------------------| - |
| `AssemblyName` | Volitelný parametr `String`.<br /><br /> Určuje `Name` pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, název je odvozen z parametrů `EntryPoint` nebo `InputManifest`. Pokud se název nedá odvodit, úloha vyvolá chybu. |
| `AssemblyVersion` | Volitelný parametr `String`.<br /><br /> Určuje `Version` pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, úloha použije hodnotu "1.0.0.0". |
| `CreateDesktopShortcut` | Volitelný parametr `Boolean`.<br /><br /> Pokud má hodnotu true, vytvoří se na ploše během instalace aplikace ClickOnce ikona. |
| `DeploymentUrl` | Volitelný parametr `String`.<br /><br /> Určuje umístění aktualizace pro aplikaci. Pokud tento parametr není zadán, není pro aplikaci definováno žádné umístění aktualizace. Pokud je však parametr `UpdateEnabled` `true`, je nutné zadat umístění aktualizace. Zadaná hodnota by měla být úplná adresa URL nebo cesta UNC. |
| `Description` | Volitelný parametr `String`.<br /><br /> Určuje volitelný popis aplikace. |
| `DisallowUrlActivation` | Volitelný parametr `Boolean`.<br /><br /> Určuje, zda má být aplikace spouštěna automaticky při otevření prostřednictvím adresy URL. Pokud je tento parametr `true`, aplikaci lze spustit pouze z nabídky **Start** . Výchozí hodnota tohoto parametru je `false`. Tento vstup platí pouze v případě, že je hodnota parametru `Install` `true`. |
| `EntryPoint` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Označuje vstupní bod pro vygenerované sestavení manifestu. V případě manifestu nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] určuje tento vstup manifest [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace.<br /><br />Pokud není zadán parametr úlohy `EntryPoint`, je značka `<customHostSpecified>` vložena jako podřízený prvek značky `<entryPoint>`, například:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Můžete přidat závislosti knihoven DLL do manifestu aplikace pomocí následujících kroků:<br /><br /> 1. vyřešte odkazy na sestavení voláním <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>.<br />2. předání výstupu předchozí úlohy a samotného sestavení do <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3. předejte závislosti pomocí parametru `Dependencies` pro <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>. |
| `ErrorReportUrl` | Volitelný parametr <xref:System.String?displayProperty=fullName>.<br /><br /> Určuje adresu URL webové stránky, která se zobrazí v dialogových oknech během instalace ClickOnce. |
| `InputManifest` | Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Označuje vstupní dokument XML, který bude sloužit jako základ pro generátor manifestu. To umožňuje, aby se strukturovaná data, jako jsou definice vlastních manifestů, projevila ve výstupním manifestu. Kořenový element v dokumentu XML musí být uzlem sestavení v oboru názvů asmv1. |
| `Install` | Volitelný parametr `Boolean`.<br /><br /> Určuje, jestli je aplikace nainstalovaná aplikace nebo aplikace jenom v režimu online. Je-li tento parametr `true`, aplikace bude nainstalována v nabídce **Start** uživatele a lze ji odebrat pomocí dialogového okna **Přidat nebo odebrat programy** . Pokud je tento parametr `false`, aplikace je určena pro online použití z webové stránky. Výchozí hodnota tohoto parametru je `true`. |
| `MapFileExtensions` | Volitelný parametr `Boolean`.<br /><br /> Určuje, zda je použito mapování přípon názvu souboru *. deploy* . Pokud je tento parametr `true`, všechny programové soubory se publikují s příponou *. deploy* . Tato možnost je užitečná pro zabezpečení webového serveru k omezení počtu přípon názvů souborů, které je potřeba odblokovat, aby bylo možné [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení aplikace. Výchozí hodnota tohoto parametru je `false`. |
| `MaxTargetPath` | Volitelný parametr `String`.<br /><br /> Určuje maximální povolenou délku cesty k souboru ve [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení aplikace. Je-li tento parametr zadán, bude na základě tohoto limitu kontrolována délka každé cesty souboru v aplikaci. Všechny položky, které překračují limit, způsobí upozornění sestavení. Pokud tento vstup není zadán nebo je nula, žádná kontrola se neprovádí. |
| `MinimumRequiredVersion` | Volitelný parametr `String`.<br /><br /> Určuje, jestli uživatel může aktualizaci přeskočit. Pokud má uživatel verzi, která je menší než minimální požadovaná verze, nebude mít možnost tuto aktualizaci přeskočit. Tento vstup platí pouze v případě, že je hodnota parametru `Install` `true`. |
| `OutputManifest` | Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje název vygenerovaného výstupního souboru manifestu. Pokud tento parametr není zadán, název výstupního souboru je odvozen z identity generovaného manifestu. |
| `Platform` | Volitelný parametr `String`.<br /><br /> Určuje cílovou platformu aplikace. Tento parametr může mít následující hodnoty:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Výchozí hodnota je `AnyCPU`. |
| `Product` | Volitelný parametr `String`.<br /><br /> Určuje název aplikace. Pokud tento parametr není zadán, název je odvozen z identity generovaného manifestu. Tento název se používá pro název zástupce v nabídce **Start** a je součástí názvu, který se zobrazí v dialogovém okně **Přidat nebo odebrat programy** . |
| `Publisher` | Volitelný parametr `String`.<br /><br /> Určuje vydavatele aplikace. Pokud tento parametr není zadán, je název odvozen od registrovaného uživatele nebo z identity generovaného manifestu. Tento název se používá pro název složky v nabídce **Start** a je součástí názvu, který se zobrazí v dialogovém okně **Přidat nebo odebrat programy** . |
| `SuiteNamel` | Volitelný parametr `String`.<br /><br /> Určuje název složky v nabídce **Start** , kde se aplikace nachází po nasazení ClickOnce. |
| `SupportUrl` | Volitelný parametr `String`.<br /><br /> Určuje odkaz, který se zobrazí v dialogovém okně **Přidat nebo odebrat programy** pro aplikaci. Zadaná hodnota by měla být úplná adresa URL nebo cesta UNC. |
| `TargetCulture` | Volitelný parametr `String`.<br /><br /> Určuje jazykovou verzi aplikace a určuje pole `Language` identity sestavení pro generovaný manifest. Není-li tento parametr zadán, předpokládá se, že aplikace je invariantní jazykové verze. |
| `TrustUrlParameters` | Volitelný parametr `Boolean`.<br /><br /> Určuje, zda mají být pro aplikaci k dispozici parametry řetězce dotazu adresy URL. Výchozí hodnota tohoto parametru je `false`, což znamená, že parametry nebudou k dispozici pro aplikaci. |
| `UpdateEnabled` | Volitelný parametr `Boolean`.<br /><br /> Určuje, zda je aplikace povolena pro aktualizace. Výchozí hodnota tohoto parametru je `false`. Tento parametr platí pouze v případě, že je hodnota parametru `Install` `true`. |
| `UpdateInterval` | Volitelný parametr `Int32`.<br /><br /> Určuje interval aktualizace pro aplikaci. Výchozí hodnota tohoto parametru je nula. Tento parametr platí pouze v případě, že jsou hodnoty parametrů `Install` a `UpdateEnabled` `true`. |
| `UpdateMode` | Volitelný parametr `String`.<br /><br /> Určuje, zda mají být aktualizace zkontrolovány v popředí před spuštěním aplikace nebo na pozadí, jako je aplikace spuštěna. Tento parametr může mít následující hodnoty:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Výchozí hodnota tohoto parametru je `Background`. Tento parametr platí pouze v případě, že jsou hodnoty parametrů `Install` a `UpdateEnabled` `true`. |
| `UpdateUnit` | Volitelný parametr `String`.<br /><br /> Určuje jednotky pro parametr `UpdateInterval`. Tento parametr může mít následující hodnoty:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Tento parametr platí pouze v případě, že jsou hodnoty parametrů `Install` a `UpdateEnabled` `true`. |

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.GenerateManifestBase> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam parametrů třídy Task naleznete v tématu [základní třída Task](../msbuild/task-base-class.md).

## <a name="see-also"></a>Viz také:

- [Úlohy](../msbuild/msbuild-tasks.md)
- [GenerateApplicationManifest – – úloha](../msbuild/generateapplicationmanifest-task.md)
- [SignFile – – úloha](../msbuild/signfile-task.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
