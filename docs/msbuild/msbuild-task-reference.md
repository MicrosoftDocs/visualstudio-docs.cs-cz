---
title: Referenční dokumentace úlohy nástroje MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbec3c7c020bae0e94bc16bdb1fe9740a36a93ae
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865320"
---
# <a name="msbuild-task-reference"></a>Referenční dokumentace úlohy nástroje MSBuild

Úlohy poskytují kód, který se spouští během procesu sestavení. Úlohy v následujícím seznamu jsou součástí nástroje MSBuild. Po instalaci C++ úlohy jsou k dispozici další úlohy, které se používají k sestavení C++ projektů. Další informace najdete v tématu [ C++ úlohy](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Kromě parametrů uvedených v tématech v této části má každá úloha také následující parametry:

| Parametr | Popis |
|-------------------| - |
| `Condition` | Volitelný parametr `String`.<br /><br /> Výraz `Boolean`, který modul MSBuild používá k určení, zda bude tato úloha spuštěna. Informace o podmínkách podporovaných nástrojem MSBuild naleznete v tématu [podmínky](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Volitelný parametr. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Pokud se úloha nezdařila, následné úkoly v [cílovém](../msbuild/target-element-msbuild.md) elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za upozornění.<br />-   **ErrorAndContinue**. Pokud se úloha nezdařila, následné úkoly v prvku `Target` a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Pokud se úloha nezdařila, zbývající úkoly v prvku `Target` a sestavení nejsou provedeny a celý `Target` element a sestavení se považuje za neúspěšné.<br /><br /> Verze .NET Framework před 4,5 podporují pouze hodnoty `true` a `false`.<br /><br /> Další informace najdete v tématu [Postupy: ignorování chyb v úlohách](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>V tomto oddílu

- [Základní třída úlohy](../msbuild/task-base-class.md)

 Přidá několik parametrů k úkolům odvozeným od třídy <xref:Microsoft.Build.Utilities.Task>. Není určeno k použití přímo.

- [Základní třída TaskExtension –](../msbuild/taskextension-base-class.md)

 Přidá několik parametrů k úkolům odvozeným od třídy <xref:Microsoft.Build.Tasks.TaskExtension>. Není určeno k použití přímo.

- [Základní třída ToolTaskExtension –](../msbuild/tooltaskextension-base-class.md)

 Přidá několik parametrů k úkolům odvozeným od třídy <xref:Microsoft.Build.Tasks.ToolTaskExtension>. Není určeno k použití přímo.

- [AL (Assembly Linker) – úloha](../msbuild/al-assembly-linker-task.md)

 Vytvoří sestavení s manifestem z jednoho nebo více souborů, které jsou buď moduly, nebo soubory prostředků.

- [AspNetCompiler – – úloha](../msbuild/aspnetcompiler-task.md)

 Zabalí *Aspnet_compiler. exe*, nástroj pro předkompilování aplikací ASP.NET.

- [AssignCulture – – úloha](../msbuild/assignculture-task.md)

 Přiřadí identifikátory jazykové verze k položkám.

- [AssignProjectConfiguration – – úloha](../msbuild/assignprojectconfiguration-task.md)

 Přijme seznam konfiguračních řetězců a přiřadí je zadaným projektům.

- [AssignTargetPath – – úloha](../msbuild/assigntargetpath-task.md)

 Přijme seznam souborů a přidá atributy `<TargetPath>`, pokud již nejsou zadány.

- [CallTarget – – úloha](../msbuild/calltarget-task.md)

 Vyvolá cíl v souboru projektu.

- [CombinePath – – úloha](../msbuild/combinepath-task.md)

 Zkombinuje zadané cesty do jedné cesty.

- [ConvertToAbsolutePath – – úloha](../msbuild/converttoabsolutepath-task.md)

 Převede relativní cestu nebo odkaz na absolutní cestu.

- [Kopírovat úlohu](../msbuild/copy-task.md)

 Zkopíruje soubory do nového umístění.

- [CreateCSharpManifestResourceName – – úloha](../msbuild/createcsharpmanifestresourcename-task.md)

 C#Vytvoří název manifestu stylu z daného názvu souboru *. resx* nebo jiného prostředku.

- [CreateItem – – úloha](../msbuild/createitem-task.md)

 Naplní kolekce položek ze vstupních položek a umožní kopírování položek z jednoho seznamu do jiného.

- [CreateProperty – – úloha](../msbuild/createproperty-task.md)

 Naplní vlastnosti ze vstupních hodnot a povoluje zkopírování hodnot z jedné vlastnosti nebo řetězce do jiného.

- [CreateVisualBasicManifestResourceName – – úloha](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Vytvoří název manifestu ve stylu Visual Basic z daného názvu souboru *. resx* nebo jiného prostředku.

- [CSc – úloha](../msbuild/csc-task.md)

 Vyvolá kompilátor vizuálu C# pro vytváření spustitelných souborů, knihoven DLL nebo modulů kódu.

- [Odstranit úlohu](../msbuild/delete-task.md)

 Odstraní zadané soubory.

- [DownloadFile – úloha](../msbuild/downloadfile-task.md)

 Stáhne soubor do zadaného umístění.

- [Chybová úloha](../msbuild/error-task.md)

 Zastaví sestavení a zaznamená chybu na základě vyhodnoceného podmíněného příkazu.

- [Exec – úloha](../msbuild/exec-task.md)

 Spustí zadaný program nebo příkaz se zadanými argumenty.

- [FindAppConfigFile – – úloha](../msbuild/findappconfigfile-task.md)

 Vyhledá soubor *App. config* , pokud existuje, v uvedených seznamech.

- [FindInList – – úloha](../msbuild/findinlist-task.md)

 Najde položku v zadaném seznamu, která má odpovídající itemspec.

- [FindUnderPath – – úloha](../msbuild/findunderpath-task.md)

 Určuje, které položky v zadané kolekci položek existují v zadané složce a všech jejích podsložkách.

- [FormatUrl – – úloha](../msbuild/formaturl-task.md)

 Převede adresu URL na správný formát adresy URL.

- [FormatVersion – – úloha](../msbuild/formatversion-task.md)

 Připojí číslo revize k číslu verze.

- [GenerateApplicationManifest – – úloha](../msbuild/generateapplicationmanifest-task.md)

 Generuje manifest aplikace ClickOnce nebo nativní manifest.

- [GenerateBootstrapper – – úloha](../msbuild/generatebootstrapper-task.md)

 Poskytuje automatizovaný způsob detekce, stažení a instalace aplikace a jejích požadavků.

- [GenerateDeploymentManifest – – úloha](../msbuild/generatedeploymentmanifest-task.md)

 Generuje manifest nasazení ClickOnce.

- [GenerateResource – – úloha](../msbuild/generateresource-task.md)

 Převede soubory *. txt* a *. resx* do binárních souborů *. Resources* modulu CLR (Common Language Runtime).

- [GenerateTrustInfo – – úloha](../msbuild/generatetrustinfo-task.md)

 Generuje vztah důvěryhodnosti aplikace ze základního manifestu a z parametrů `TargetZone` a `ExcludedPermissions`.

- [GetAssemblyIdentity – úloha](../msbuild/getassemblyidentity-task.md)

 Načte z určených souborů identity sestavení a vypíše informace o identitě.

- [GetFileHash – úloha](../msbuild/getfilehash-task.md)

 Vypočítá kontrolní součet obsahu souboru nebo sady souborů.

- [GetFrameworkPath – – úloha](../msbuild/getframeworkpath-task.md)

 Načte cestu k sestavením .NET Framework.

- [GetFrameworkSdkPath – – úloha](../msbuild/getframeworksdkpath-task.md)

 Načte cestu k sadě Windows Software Development Kit (SDK).

- [GetReferenceAssemblyPaths – – úloha](../msbuild/getreferenceassemblypaths-task.md)

 Vrátí cesty referenčního sestavení různých rozhraní.

- [LC – úloha](../msbuild/lc-task.md)

 Vygeneruje soubor *. License* ze souboru *. licx* .

- [MakeDir – – úloha](../msbuild/makedir-task.md)

 Vytvoří adresáře a v případě potřeby i všechny nadřazené adresáře.

- [Úloha zprávy](../msbuild/message-task.md)

 Zaprotokoluje zprávu během sestavení.

- [Přesunout úkol](../msbuild/move-task.md)

 Přesune soubory do nového umístění.

- [MSBuild – úloha](../msbuild/msbuild-task.md)

 Vytvoří projekty MSBuild z jiného projektu MSBuild.

- [ReadLinesFromFile – – úloha](../msbuild/readlinesfromfile-task.md)

 Přečte seznam položek z textového souboru.

- [RegisterAssembly – – úloha](../msbuild/registerassembly-task.md)

 Přečte metadata v rámci zadaného sestavení a přidá nezbytné položky do registru.

- [RemoveDir – – úloha](../msbuild/removedir-task.md)

 Odebere zadané adresáře a všechny jeho soubory a podadresáře.

- [RemoveDuplicates – – úloha](../msbuild/removeduplicates-task.md)

 Odstraní duplicitní položky ze zadané kolekce položek.

- [Requiresframework35sp1assembly – – úloha](../msbuild/requiresframework35sp1assembly-task.md)

 Určuje, jestli aplikace vyžaduje .NET Framework 3,5 SP1.

- Úloha ResGen

 Zastaralé. Úkol [úlohy GenerateResource –](../msbuild/generateresource-task.md) použijte k převodu souborů *. txt* a *. resx* do a z binárního souboru *. Resources* modulu CLR.

- [ResolveAssemblyReference – – úloha](../msbuild/resolveassemblyreference-task.md)

 Určuje všechna sestavení, která závisí na zadaných sestaveních.

- [ResolveComReference – – úloha](../msbuild/resolvecomreference-task.md)

 Převezme seznam jednoho nebo více názvů knihoven typů nebo souborů *. tlb* a přeloží tyto knihovny typů do umístění na disku.

- [ResolveKeySource – – úloha](../msbuild/resolvekeysource-task.md)

 Určuje zdroj klíče se silným názvem.

- [ResolveManifestFiles – – úloha](../msbuild/resolvemanifestfiles-task.md)

 Řeší následující položky v procesu sestavení do souborů pro generování manifestu: sestavené položky, závislosti, satelity, obsah, symboly ladění a dokumentace.

- [ResolveNativeReference – – úloha](../msbuild/resolvenativereference-task.md)

 Přeloží nativní odkazy.

- [ResolveNonMSBuildProjectOutput – – úloha](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Určuje výstupní soubory pro odkazy na projekt, které nejsou v nástroji MSBuild.

- [SGen – úloha](../msbuild/sgen-task.md)

 Vytvoří sestavení serializace XML pro typy v zadaném sestavení.

- [SignFile – – úloha](../msbuild/signfile-task.md)

 Podepíše zadaný soubor pomocí zadaného certifikátu.

- [Dotyková úloha](../msbuild/touch-task.md)

 Nastaví dobu přístupu a úprav souborů.

- [UnregisterAssembly – – úloha](../msbuild/unregisterassembly-task.md)

 Zruší registraci zadaných sestavení pro účely zprostředkovatele komunikace s objekty COM.

- [Rozbalit úlohu](../msbuild/unzip-task.md)

 Rozbalí archiv *zip* do zadaného umístění.

- [UpdateManifest – – úloha](../msbuild/updatemanifest-task.md)

 Aktualizuje vybrané vlastnosti v manifestu a znovu se podepíše.

- [Vbc – úloha](../msbuild/vbc-task.md)

 Vyvolá kompilátor Visual Basic pro vytváření spustitelných souborů, knihoven DLL nebo modulů kódu.

- [VerifyFileHash – úloha](../msbuild/verifyfilehash-task.md)

 Ověřuje, že soubor odpovídá očekávané hodnotě hash souboru.

- [Úloha upozornění](../msbuild/warning-task.md)

 Zaznamená upozornění během sestavení na základě vyhodnoceného podmíněného příkazu.

- [WriteCodeFragment – – úloha](../msbuild/writecodefragment-task.md)

 Generuje dočasný soubor kódu pomocí zadaného vygenerovaného fragmentu kódu. Neodstraní soubor.

- [WriteLinesToFile – – úloha](../msbuild/writelinestofile-task.md)

 Zapíše zadané položky do zadaného textového souboru.

- [XmlPeek – – úloha](../msbuild/xmlpeek-task.md)

 Vrátí hodnoty určené dotazem XPath ze souboru XML.

- [XmlPoke – – úloha](../msbuild/xmlpoke-task.md)

 Nastaví hodnoty určené dotazem XPath do souboru XML.

- [XslTransformation – – úloha](../msbuild/xsltransformation-task.md)

 Transformuje vstup XML pomocí *Extensible Stylesheet Language Transformation* (XSLT) nebo zkompilovaného souboru XSLT a výstupy na výstupní zařízení nebo soubor.

- [ZipDirectory – úloha](../msbuild/zipdirectory-task.md)

 Vytvoří archiv *zip* z obsahu adresáře.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Zápis úlohy](../msbuild/task-writing.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
