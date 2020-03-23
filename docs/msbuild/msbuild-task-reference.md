---
title: Odkaz na úkol msbuild | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865320"
---
# <a name="msbuild-task-reference"></a>Odkaz na úkol MSBuild

Úkoly poskytují kód, který se spustí během procesu sestavení. Úkoly v následujícím seznamu jsou zahrnuty s MSBuild. Při instalaci zatížení Jazyka C++ jsou k dispozici další úkoly, které se používají k vytváření projektů jazyka C++. Další informace naleznete v tématu [Úkoly jazyka C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Kromě parametrů uvedených v tématech v této části má každý úkol také následující parametry:

| Parametr | Popis |
|-------------------| - |
| `Condition` | Volitelný `String` parametr.<br /><br /> Výraz, `Boolean` který modul MSBuild používá k určení, zda bude tato úloha provedena. Informace o podmínkách podporovaných msbuild, naleznete v [tématu Podmínky](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Volitelný parametr. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Pokud úloha selže, následné úkoly v [Target](../msbuild/target-element-msbuild.md) element a sestavení pokračovat v provádění a všechny chyby z úkolu jsou považovány za upozornění.<br />-   **ErrorAndContinue**. Pokud úloha selže, následné `Target` úkoly v prvku a sestavení pokračovat v provádění a všechny chyby z úkolu jsou považovány za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Pokud úloha selže, zbývající úkoly v elementu `Target` a sestavení nejsou `Target` provedeny a celý prvek a sestavení se považuje za neúspěšné.<br /><br /> Verze rozhraní .NET Framework před 4.5 `true` `false` podporovaly pouze hodnoty a.<br /><br /> Další informace naleznete v [tématu Postup: Ignorovat chyby v úkolech](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>V tomto oddílu

- [Základní třída úkolu](../msbuild/task-base-class.md)

 Přidá několik parametrů k úkolům, <xref:Microsoft.Build.Utilities.Task> které jsou odvozeny z třídy. Není určeno k přímému použití.

- [Základní třída TaskExtension](../msbuild/taskextension-base-class.md)

 Přidá několik parametrů k úkolům, <xref:Microsoft.Build.Tasks.TaskExtension> které jsou odvozeny z třídy. Není určeno k přímému použití.

- [Základní třída ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)

 Přidá několik parametrů k úkolům, <xref:Microsoft.Build.Tasks.ToolTaskExtension> které jsou odvozeny z třídy. Není určeno k přímému použití.

- [Úloha AL (Assembly Linker)](../msbuild/al-assembly-linker-task.md)

 Vytvoří sestavení s manifestem z jednoho nebo více souborů, které jsou moduly nebo soubory prostředků.

- [Úloha aspNetCompiler](../msbuild/aspnetcompiler-task.md)

 Zalomí *aspnet_compiler.exe*, nástroj pro předkompilaci ASP.NET aplikací.

- [Úkol AssignCulture](../msbuild/assignculture-task.md)

 Přiřadí identifikátory jazykové verze k položkám.

- [Přiřazení úkolu Konfigurace projektu](../msbuild/assignprojectconfiguration-task.md)

 Přijme seznam konfiguračních řetězců a přiřadí je k určeným projektům.

- [Přiřadit úkol TargetPath](../msbuild/assigntargetpath-task.md)

 Přijme seznam souborů a `<TargetPath>` přidá atributy, pokud ještě nejsou zadány.

- [Úkol CallTarget](../msbuild/calltarget-task.md)

 Vyvolá cíl v souboru projektu.

- [Úloha CombinePath](../msbuild/combinepath-task.md)

 Zkombinuje zadané cesty do jedné cesty.

- [Úloha PřevéstnaAbsolutePath](../msbuild/converttoabsolutepath-task.md)

 Převede relativní cestu nebo odkaz na absolutní cestu.

- [Kopírovat úkol](../msbuild/copy-task.md)

 Zkopíruje soubory do nového umístění.

- [Úloha CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md)

 Vytvoří název manifestu ve stylu C# z daného názvu souboru *RESX* nebo jiného prostředku.

- [Úkol Vytvořit položku](../msbuild/createitem-task.md)

 Naplní kolekce položek ze vstupních položek a umožní kopírování položek z jednoho seznamu do druhého.

- [CreateProperty – úloha](../msbuild/createproperty-task.md)

 Naplní vlastnosti ze vstupních hodnot, což umožňuje zkopírovat hodnoty z jedné vlastnosti nebo řetězce do jiného.

- [Úloha VytvořitVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Vytvoří název manifestu ve stylu jazyka Visual Basic z daného názvu souboru *RESX* nebo jiného prostředku.

- [Úkol CsC](../msbuild/csc-task.md)

 Vyvolá kompilátor Visual C# k vytvoření spustitelných souborů, knihoven dynamických spojů nebo modulů kódu.

- [Odstranit úkol](../msbuild/delete-task.md)

 Odstraní zadané soubory.

- [Úloha DownloadFile](../msbuild/downloadfile-task.md)

 Stáhne soubor do zadaného umístění.

- [Chybová úloha](../msbuild/error-task.md)

 Zastaví sestavení a zaznamená chybu na základě vyhodnoceného podmíněného příkazu.

- [Exec úkol](../msbuild/exec-task.md)

 Spustí zadaný program nebo příkaz se zadanými argumenty.

- [Úloha FindAppConfigFile](../msbuild/findappconfigfile-task.md)

 Vyhledá soubor *app.config,* pokud existuje, v poskytnutých seznamech.

- [Úloha NajítInList](../msbuild/findinlist-task.md)

 Vyhledá položku v zadaném seznamu, který má odpovídající itemspec.

- [Úloha FindUnderPath](../msbuild/findunderpath-task.md)

 Určuje, které položky v zadané kolekci položek existují v zadané složce a ve všech jejích podsložkách.

- [Úloha FormatUrl](../msbuild/formaturl-task.md)

 Převede adresu URL na správný formát adresy URL.

- [Úloha FormatVersion](../msbuild/formatversion-task.md)

 Připojí číslo revize k číslu verze.

- [Úloha GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)

 Generuje manifest aplikace ClickOnce nebo nativní manifest.

- [Úloha GenerateBootstrapper](../msbuild/generatebootstrapper-task.md)

 Poskytuje automatizovaný způsob, jak zjistit, stáhnout a nainstalovat aplikaci a její požadavky.

- [Úloha GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)

 Generuje manifest nasazení ClickOnce.

- [Úloha Generovat zdroj](../msbuild/generateresource-task.md)

 Převede soubory *TXT* a *Resx* na soubory s *binárními prostředky .resources* v běžném jazyce.

- [Úloha Generovat důvěryhodnou informaci](../msbuild/generatetrustinfo-task.md)

 Generuje vztah důvěryhodnosti aplikace ze základního `TargetZone` `ExcludedPermissions` manifestu a z parametrů a.

- [Úloha GetAssemblyIdentity](../msbuild/getassemblyidentity-task.md)

 Načte identity sestavení ze zadaných souborů a výstupy informace o identitě.

- [Úloha GetFileHash](../msbuild/getfilehash-task.md)

 Vypočítá kontrolní součty obsahu souboru nebo sady souborů.

- [Úloha GetFrameworkPath](../msbuild/getframeworkpath-task.md)

 Načte cestu k sestavením rozhraní .NET Framework.

- [Úloha GetFrameworkSdkPath](../msbuild/getframeworksdkpath-task.md)

 Načte cestu k sada Windows Software Development Kit (SDK).

- [Úloha GetReferenceAssemblyPaths](../msbuild/getreferenceassemblypaths-task.md)

 Vrátí cesty referenčního sestavení různých rámců.

- [Lc úkol](../msbuild/lc-task.md)

 Generuje soubor *.license* ze souboru *LICX.*

- [Úloha MakeDir](../msbuild/makedir-task.md)

 Vytvoří adresáře a v případě potřeby všechny nadřazené adresáře.

- [Úkol zprávy](../msbuild/message-task.md)

 Zaznamená zprávu během sestavení.

- [Přesunout úkol](../msbuild/move-task.md)

 Přesune soubory do nového umístění.

- [Úloha MSBuild](../msbuild/msbuild-task.md)

 Vytvoří projekty MSBuild z jiného projektu MSBuild.

- [Úloha ReadLinesFromFile](../msbuild/readlinesfromfile-task.md)

 Načte seznam položek z textového souboru.

- [Úkol RegisterAssembly](../msbuild/registerassembly-task.md)

 Přečte metadata v rámci zadaného sestavení a přidá potřebné položky do registru.

- [Úkol OdebratDir](../msbuild/removedir-task.md)

 Odebere zadané adresáře a všechny jejich soubory a podadresáře.

- [Úkol Odebrat duplikáty](../msbuild/removeduplicates-task.md)

 Odebere duplicitní položky z zadané kolekce položek.

- [VyžadujeFramework35SP1Sestava úkol](../msbuild/requiresframework35sp1assembly-task.md)

 Určuje, zda aplikace vyžaduje rozhraní .NET Framework 3.5 SP1.

- Úloha resgenu

 Zastaralé. Úloha [Generovat prostředek](../msbuild/generateresource-task.md) slouží k převodu souborů *TXT* a *Resx* do a ze souborů *binárních zdrojů* s běžným jazykem a z nich.

- [Úkol ResolveAssemblyReference](../msbuild/resolveassemblyreference-task.md)

 Určuje všechna sestavení, která závisí na určených sestaveních.

- [Úloha ResolveComReference](../msbuild/resolvecomreference-task.md)

 Pořídí seznam jednoho nebo více názvů knihovny typů nebo souborů *TLB* a přeloizuje tyto knihovny typů do umístění na disku.

- [Úloha ResolveKeySource](../msbuild/resolvekeysource-task.md)

 Určuje zdroj klíče silného názvu.

- [VyřešitManifestFiles, úloha](../msbuild/resolvemanifestfiles-task.md)

 Řeší následující položky v procesu sestavení na soubory pro generování manifestu: vytvořené položky, závislosti, satelity, obsah, ladicí symboly a dokumentace.

- [Úkol ResolveNativeReference](../msbuild/resolvenativereference-task.md)

 Řeší nativní odkazy.

- [ResolveNonMSBuildProjectOutput úkol](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Určuje výstupní soubory pro odkazy na projekt y jiné než MSBuild.

- [Úkol SGen](../msbuild/sgen-task.md)

 Vytvoří sestavení serializace XML pro typy v zadaném sestavení.

- [Úloha SignFile](../msbuild/signfile-task.md)

 Podepisuje zadaný soubor pomocí zadaného certifikátu.

- [Dotyková úloha](../msbuild/touch-task.md)

 Nastaví dobu přístupu a úprav souborů.

- [Zrušit registraciÚloha sestavení](../msbuild/unregisterassembly-task.md)

 Zruší registraci zadaných sestavení pro účely interop com.

- [Rozbalit úkol](../msbuild/unzip-task.md)

 Rozbalí archiv *ZIP* do zadaného umístění.

- [Úkol Aktualizovat manifest](../msbuild/updatemanifest-task.md)

 Aktualizuje vybrané vlastnosti v manifestu a odstoupí.

- [Úloha Vbc](../msbuild/vbc-task.md)

 Vyvolá kompilátor jazyka K vytvoření spustitelných souborů, knihoven s dynamickými spoji nebo modulů kódu.

- [Úloha VerifyFileHash](../msbuild/verifyfilehash-task.md)

 Ověří, zda soubor odpovídá očekávané hodnotě hash souboru.

- [Warning – úloha](../msbuild/warning-task.md)

 Protokoluje upozornění během sestavení na základě vyhodnoceného podmíněného příkazu.

- [Úloha WriteCodeFragment](../msbuild/writecodefragment-task.md)

 Generuje dočasný soubor kódu pomocí zadaného fragmentu generovaného kódu. Neodstraní soubor.

- [Úloha WriteLinesToFile](../msbuild/writelinestofile-task.md)

 Zapíše zadané položky do zadaného textového souboru.

- [XmlPeek úkol](../msbuild/xmlpeek-task.md)

 Vrátí hodnoty určené dotazem XPath ze souboru XML.

- [Úloha XmlPoke](../msbuild/xmlpoke-task.md)

 Nastaví hodnoty určené dotazem XPath do souboru XML.

- [Úloha XslTransformace](../msbuild/xsltransformation-task.md)

 Transformuje vstup XML pomocí *transformace jazyka extensible stylesheet* (XSLT) nebo zkompilované XSLT a výstupy do výstupního zařízení nebo souboru.

- [Úloha ZipDirectory](../msbuild/zipdirectory-task.md)

 Vytvoří archiv *ZIP* z obsahu adresáře.

## <a name="see-also"></a>Viz také

- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Psaní úkolů](../msbuild/task-writing.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
