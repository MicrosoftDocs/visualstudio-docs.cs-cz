---
title: Společné vlastnosti projektu MSBuild | Dokumenty společnosti Microsoft
ms.date: 01/18/2018
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece57a102851efe0198f8993b60dba8e0eae6dec
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634419"
---
# <a name="common-msbuild-project-properties"></a>Běžné vlastnosti projektu MSBuild

V následující tabulce jsou uvedeny často používané vlastnosti, které jsou definovány v souborech projektu sady Visual Studio nebo zahrnuty do souborů *.targets,* které msbuild poskytuje.

 Soubory projektu v sadě Visual Studio (*.csproj*, *.vbproj*, *.vcxproj*a další) obsahují kód XML MSBuild, který se spustí při vytváření projektu pomocí rozhraní IDE. Projekty obvykle importují jeden nebo více souborů *.targets* k definování jejich procesu sestavení. Další informace naleznete v tématu [MSBuild .targets files](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Seznam společných vlastností a parametrů

| Název vlastnosti nebo parametru | Popis |
|------------------------------------| - |
| Další libpathy | Určuje další složky, ve kterých by kompilátory měly hledat referenční sestavení. |
| Přidejte moduly | Způsobí, že kompilátor zpřístupnit všechny informace o typu ze zadaných souborů pro projekt, který kompilaci. Tato vlastnost je `/addModules` ekvivalentní přepínač kompilátoru. |
| ALToolPath | Cesta, kde lze nalézt *AL.exe.* Tato vlastnost přepíše aktuální verzi *souboru AL.exe* a povolí použití jiné verze. |
| Ikona aplikace | Soubor ikony *.ico,* který má být předáván kompilátoru pro vložení jako ikonu Win32. Vlastnost je ekvivalentní `/win32icon` přepínač kompilátoru. |
| ApplicationManifest | Určuje cestu k souboru, který se používá ke generování externích informací o manifestu řízení uživatelských účtů (UAC). Platí pouze pro projekty sady Visual Studio, které cílí na systém Windows Vista.<br /><br /> Ve většině případů je vložen manifest. Pokud však použijete nasazení com nebo ClickOnce zdarma registrace, může být manifest externí soubor, který je nainstalován společně s sestaveními aplikací. Další informace naleznete v vlastnosti NoWin32Manifest v tomto tématu. |
| Soubor OriginatorKeyFile sestavení | Určuje soubor, který se používá k podepsání sestavení (*.snk* nebo *.pfx*) a který je předán [úkolu ResolveKeySource](../msbuild/resolvekeysource-task.md) ke generování skutečného klíče, který se používá k podepsání sestavení. |
| AssemblySearchPaths | Seznam umístění pro vyhledávání během rozlišení sestavení referenční sestavení. Pořadí, ve kterém se cesty zobrazují v tomto seznamu, má smysl, protože cesty uvedené výše mají přednost před pozdějšími položkami. |
| Assemblyname | Název konečného výstupního sestavení po sestavení projektu. |
| Základní adresa | Určuje základní adresu hlavního výstupního sestavení. Tato vlastnost je `/baseaddress` ekvivalentní přepínač kompilátoru. |
| BaseIntermediateOutputPath | Složka nejvyšší úrovně, kde jsou vytvořeny všechny zprostředkující výstupní složky specifické pro konfiguraci. Výchozí hodnota je `obj\`. Následující kód je příklad:`<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| Základní outputcesta | Určuje základní cestu pro výstupní soubor. Pokud je nastavena, MSBuild bude používat `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Příklad syntaxe:`<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Logická hodnota, která označuje, zda jsou odkazy na projekt vytvořeny nebo vyčištěny paralelně při použití multi-Proc MSBuild. Výchozí hodnota `true`je , což znamená, že projekty budou vytvořeny paralelně, pokud systém má více jader nebo procesorů. |
| BuildProjectReferences | Logická hodnota, která označuje, zda jsou odkazy na projekt sestaveny msbuild. Automaticky nastavte `false` na pokud vytváříte projekt v integrovaném vývojovém `true` prostředí sady Visual Studio (IDE), pokud jinak. `-p:BuildProjectReferences=false`lze zadat na příkazovém řádku, aby se zabránilo kontrole, zda jsou odkazované projekty aktuální. |
| Soubor CleanFile | Název souboru, který bude použit jako "čistá mezipaměť". Čistá mezipaměť je seznam generovaných souborů, které mají být odstraněny během operace čištění. Soubor je umístěn v cestě zprostředkující výstup procesem sestavení.<br /><br /> Tato vlastnost určuje pouze názvy souborů, které nemají informace o cestě. |
| Codepage | Určuje znakovou stránku, která má být v kompilaci používána pro všechny soubory zdrojového kódu. Tato vlastnost je `/codepage` ekvivalentní přepínač kompilátoru. |
| Soubor compilerresponsefile | Volitelný soubor odpovědí, který lze předat úlohám kompilátoru. |
| Konfigurace | Konfigurace, kterou vytváříte, buď "Ladění" nebo "Release". |
| CscToolPath | Cesta *csc.exe*, kompilátor jazyka C#. |
| CustomBeforeMicrosoftCommonTargets | Název souboru projektu nebo cíle souboru, který má být importován automaticky před importem společných cílů. |
| Symboly ladění | Logická hodnota, která označuje, zda jsou symboly generovány sestavením.<br /><br /> Nastavení **-p:DebugSymbols=false** na příkazovém řádku zakáže generování souborů symbolů databáze programů (*PDB).* |
| Typ ladění | Definuje úroveň ladicích informací, které chcete vygenerovat. Platné hodnoty jsou "úplné", "pdbonly", "přenosné", "vložené" a "žádné". |
| Definovat konstanty | Definuje konstanty podmíněného kompilátoru. Dvojice symbolů a hodnot jsou odděleny středníky a jsou určeny pomocí následující syntaxe:<br /><br /> *symbol1 = hodnota1 ; symbol2 = hodnota2*<br /><br /> Vlastnost je ekvivalentní `/define` přepínač kompilátoru. |
| Definovatladění | Logická hodnota, která označuje, zda chcete definovat konstantu LADĚNÍ. |
| Definovattrasovat | Logická hodnota, která označuje, zda chcete definovat konstantu TRACE. |
| Delaysign | Logická hodnota, která označuje, zda chcete zpoždění podepsat sestavení spíše než úplné podepisování. |
| Deterministická | Logická hodnota, která označuje, zda by měl kompilátor vyrábět identické sestavy pro identické vstupy. Tento parametr odpovídá `/deterministic` přepínači kompilátorů *vbc.exe* a *csc.exe.* |
| Upozornění na zakázané | Potlačí zadaná upozornění. Musí být zadána pouze číselná část identifikátoru upozornění. Více upozornění jsou odděleny středníky. Tento parametr odpovídá `/nowarn` přepínači kompilátoru *vbc.exe.* |
| Zakázat funkci DisableUpToDateCheck | Logická hodnota, která platí pouze pro Visual Studio. Správce sestavení sady Visual Studio používá proces s názvem FastUpToDateCheck k určení, zda projekt musí být znovu sestaven, aby byl aktuální. Tento proces je rychlejší než pomocí MSBuild k určení tohoto. Nastavení Vlastnost disableFastUpToDateCheck `true` umožňuje obejít správce sestavení sady Visual Studio a vynutit jeho použití MSBuild k určení, zda je projekt aktuální. |
| Soubor dokumentace | Název souboru, který je generován jako soubor dokumentace XML. Tento název obsahuje pouze název souboru a neobsahuje žádné informace o cestě. |
| Sestava chyb | Určuje, jak by měla úloha kompilátoru vykazovat interní chyby kompilátoru. Platné hodnoty jsou "výzva", "odeslat" nebo "žádné". Tato vlastnost je `/errorreport` ekvivalentní přepínač kompilátoru. |
| Adresa ExcludeDeploymentUrl | [Úloha GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md) přidá značku deploymentProvider do manifestu nasazení, pokud soubor projektu obsahuje některý z následujících prvků:<br /><br /> - UpdateUrl<br />- InstallUrl<br />- PublishUrl<br /><br /> Pomocí ExcludeDeploymentUrl však můžete zabránit přidání značky deploymentProvider do manifestu nasazení i v případě, že jsou zadány některé z výše uvedených adres URL. Chcete-li to provést, přidejte do souboru projektu následující vlastnost:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Poznámka:**  ExcludeDeploymentUrl není vystavena v IDE sady Visual Studio a lze nastavit pouze ruční úpravou souboru projektu. Nastavení této vlastnosti nemá vliv na publikování v rámci sady Visual Studio; to znamená, že značka deploymentProvider bude stále přidána do adresy URL určené publishurl. |
| Zarovnání souborů | Určuje, kde mají být v bajtech zarovnány části výstupního souboru. Platné hodnoty jsou 512, 1024, 2048, 4096, 8192. Tato vlastnost je `/filealignment` ekvivalentní přepínač kompilátoru. |
| FrameworkPathOverride | Určuje umístění souborů *mscorlib.dll* a *microsoft.visualbasic.dll*. Tento parametr je `/sdkpath` ekvivalentní přepínači kompilátoru *vbc.exe.* |
| Generovat dokumentaci | (C#, Visual Basic) Logický parametr, který označuje, zda je sestavenígenerována dokumentace. Pokud `true`sestavení generuje informace o dokumentaci a umístí je do souboru *XML* spolu s názvem spustitelného souboru nebo knihovny, kterou vytvořil avytvořil úlohu sestavení. |
| GenerateFullPaths | (C#) Generovat úplné cesty pro názvy souborů ve výstupu pomocí [-fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) kompilátormožnost. |
| Generovat serializační sestavení | Označuje, zda mají být sestavení serializace XML generována pomocí *sgen.exe*, kterou lze nastavit na zapnuto, automaticky nebo vypnuto. Tato vlastnost se používá pro sestavení, která cílí pouze na rozhraní .NET Framework. Chcete-li generovat sestavení serializace XML pro sestavení .NET Standard nebo .NET Core, odkazujte na balíček *Microsoft.XmlSerializer.Generator* NuGet. |
| IntermediateOutputPath | Úplná zprostředkující výstupní `BaseIntermediateOutputPath`cesta odvozená z aplikace , pokud není zadána žádná cesta. Například *\obj\debug\\*. |
| Název_kontejneru | Název kontejneru klíčů silného názvu. |
| Soubor KeyOriginatorFile | Název souboru klíče silného názvu. |
| Název_moduluAssembly | Název sestavení, které má být začleněn zkompilovaný modul. Vlastnost je ekvivalentní `/moduleassemblyname` přepínač kompilátoru. |
| MSBuildProjectExtensionsPath | Určuje cestu, kde jsou umístěna rozšíření projektu. Ve výchozím nastavení to má `BaseIntermediateOutputPath`stejnou hodnotu jako . |
| NoLogo | Logická hodnota, která označuje, zda má být logo kompilátoru vypnuto. Tato vlastnost je `/nologo` ekvivalentní přepínač kompilátoru. |
| NoStdLib | Logická hodnota, která označuje, zda se má vyhnout odkazování na standardní knihovnu *(mscorlib.dll).* Výchozí hodnota je `false`. |
| NoVBRuntimeReference | Logická hodnota, která označuje, zda by měl být do projektu zahrnut jako odkaz na soubor Runtime jazyka Visual Basic *(Microsoft.VisualBasic.dll).* |
| NoWin32Manifest | Logická hodnota, která označuje, zda informace o manifestu řízení uživatelských účtů (UAC) budou vloženy do spustitelného souboru aplikace. Platí pouze pro projekty sady Visual Studio, které cílí na systém Windows Vista. V projektech nasazených pomocí clickonce a registrace bez COM, tento prvek je ignorována. `False`(výchozí hodnota) určuje, že informace o manifestu řízení uživatelských účtů (UAC) budou vloženy do spustitelného souboru aplikace. `True`určuje, že informace manifestu uac nebudou vloženy.<br /><br /> Tato vlastnost platí pouze pro projekty sady Visual Studio, které cílí na systém Windows Vista. V projektech nasazených pomocí clickonce a registrace bez COM, tato vlastnost je ignorována.<br /><br /> NoWin32Manifest byste měli přidat pouze v případě, že nechcete, aby visual studio vkládalo žádné informace o manifestu do spustitelného souboru aplikace. tento proces se nazývá *virtualizace*. Chcete-li použít `<ApplicationManifest>` virtualizaci, `<NoWin32Manifest>` nastavte ve spojení s následujícím:<br /><br /> - Pro projekty jazyka, odeberte `<ApplicationManifest>` uzel. (V projektech `<NoWin32Manifest>` jazyka Visual Basic `<ApplicationManifest>` je ignorována, pokud existuje uzel.)<br />- Pro projekty `<ApplicationManifest>` Jazyka `False` `<NoWin32Manifest>` C# nastavte na a na `True`. (V projektech `<ApplicationManifest>` Jazyka `<NoWin32Manifest>`C# přepíše .)<br /> Tato vlastnost je `/nowin32manifest` ekvivalentní přepínačkompilátoru *vbc.exe*. |
| Optimalizace | Logická hodnota, která `true`při nastavení na , umožňuje optimalizace kompilátoru. Tato vlastnost je `/optimize` ekvivalentní přepínač kompilátoru. |
| OptionCompare | Určuje způsob porovnání řetězců. Platné hodnoty jsou "binární" nebo "text". Tato vlastnost je `/optioncompare` ekvivalentní přepínačkompilátoru *vbc.exe*. |
| OptionExplicit | Logická hodnota, která `true`při nastavení na , vyžaduje explicitní deklaraci proměnných ve zdrojovém kódu. Tato vlastnost je `/optionexplicit` ekvivalentní přepínač kompilátoru. |
| OptionInfer | Logická hodnota, která `true`při nastavení na , umožňuje odvození typu proměnných. Tato vlastnost je `/optioninfer` ekvivalentní přepínač kompilátoru. |
| OptionStrict | Logická hodnota, která `true`při nastavení na , způsobí, že úloha sestavení vynutit sémantiku přísného typu omezit implicitní převody typu. Tato vlastnost je `/optionstrict` ekvivalentní přepínači kompilátoru *vbc.exe.* |
| OutDir | Označuje konečné výstupní umístění pro projekt nebo řešení. Při vytváření řešení OutDir lze shromáždit více výstupů projektu v jednom umístění. Kromě toho OutDir je součástí AssemblySearchPaths slouží k řešení odkazů. Například *bin\Debug*. |
| OutputPath | Určuje cestu k výstupnímu adresáři vzhledem k adresáři projektu, například *bin\Debug*. |
| Typ výstupu | Určuje formát souboru výstupního souboru. Tento parametr může mít jednu z následujících hodnot:<br /><br /> - V knihovně. Vytvoří knihovnu kódu. (Výchozí hodnota.)<br />- Exe. Vytvoří konzolovou aplikaci.<br />- Modul. Vytvoří modul.<br />- Winexe, co se s tím zvýžela. Vytvoří program založený na systému Windows.<br /><br /> Tato vlastnost je `/target` ekvivalentní přepínači kompilátoru *vbc.exe.* |
| Přepsatsoubory ReadOnlyFiles | Logická hodnota, která označuje, zda chcete povolit sestavení přepsat soubory jen pro čtení nebo spustit chybu. |
| Mapa cesty | Určuje způsob mapování fyzických cest na názvy zdrojových cest, které kompilátor vyvodí. Tato vlastnost je `/pathmap` ekvivalentní přepínači kompilátoru *csc.exe.* |
| Soubor Pdb | Název souboru *PDB,* který vyzařujete. Tato vlastnost je `/pdb` ekvivalentní přepínači kompilátoru *csc.exe.* |
| Platforma | Operační systém, pro který vytváříte. Platné hodnoty jsou "Libovolný procesor", "x86" a "x64". |
| ProcessorArchitecture | Architektura procesoru, která se používá při překládání odkazů na sestavení. Platné hodnoty jsou "msil", "x86", "amd64" nebo "ia64". |
| Vytvořitpouzereferencesestavení | Logická hodnota, která instruuje kompilátor emitovat pouze referenční sestavení, nikoli kompilovaný kód. Nelze použít ve `ProduceReferenceAssembly`spojení s .  Tato vlastnost odpovídá `/refonly` přepínači *kompilátorů vbc.exe* a *csc.exe.* |
| ProduceReferenceAssembly | Logická hodnota, která `true` při nastavení umožňuje výrobu [referenčních sestav](/dotnet/standard/assembly/reference-assemblies) pro aktuální sestavení. `Deterministic`by `true` měla být při použití této funkce. Tato vlastnost odpovídá `/refout` přepínači *kompilátorů vbc.exe* a *csc.exe.* |
| RemoveIntegerChecks | Logická hodnota, která označuje, zda zakázat kontroly chyb přetečení celé číslo. Výchozí hodnota je `false`. Tato vlastnost je `/removeintchecks` ekvivalentní přepínači kompilátoru *vbc.exe.* |
| Rootnamespace | Kořenový obor názvů, který se má použít při pojmenování vloženého prostředku. Tento obor názvů je součástí názvu manifestu vloženého prostředku. |
| Satellite_AlgorithmId | ID algoritmu s hash em *AL.exe,* který se má použít při vytváření satelitních sestavení. |
| Satellite_BaseAddress | Základní adresa, která se má použít při sestaveních `CreateSatelliteAssemblies` satelitů specifických pro jazykovou verzi pomocí cíle. |
| Satellite_CompanyName | Název společnosti převést do *AL.exe* během generování satelitní montáže. |
| Satellite_Configuration | Název konfigurace předat do *AL.exe* během generování satelitní sestavení. |
| Satellite_Description | Popisný text předat do *AL.exe* během generování satelitní sestavení. |
| Satellite_EvidenceFile | Vloží zadaný soubor do satelitního sestavení, které má název prostředku Security.Evidence. |
| Satellite_FileVersion | Určuje řetězec pro pole Verze souboru v satelitním sestavení. |
| Satellite_Flags | Určuje hodnotu pole Příznaky v satelitním sestavení. |
| Satellite_GenerateFullPaths | Způsobí, že úloha sestavení použije absolutní cesty pro všechny soubory uvedené v chybové zprávě. |
| Satellite_LinkResource | Propojí zadané soubory prostředků se satelitním sestavením. |
| Satellite_MainEntryPoint | Určuje plně kvalifikovaný název (tj. class.method) metody, která má být používána jako vstupní bod při převodu modulu na spustitelný soubor během generování satelitního sestavení. |
| Satellite_ProductName | Určuje řetězec pro pole Produkt v satelitním sestavení. |
| Satellite_ProductVersion | Určuje řetězec pro pole ProductVersion v satelitním sestavení. |
| Satellite_TargetType | Určuje formát souboru výstupního souboru satelitního sestavení jako "knihovna", "exe" nebo "win". Výchozí hodnota je "knihovna". |
| Satellite_Title | Určuje řetězec pro pole Název v satelitním sestavení. |
| Satellite_Trademark | Určuje řetězec pro pole Ochranná známka v satelitním sestavení. |
| Satellite_Version | Určuje informace o verzi satelitního sestavení. |
| Satellite_Win32Icon | Vloží soubor ikony *.ico* do satelitního sestavení. |
| Satellite_Win32Resource | Vloží prostředek Win32 (*.res* soubor) do satelitního sestavení. |
| Sgentoolpath | Volitelná cesta nástroje, která označuje, kde získat *SGen.exe* při přepsání aktuální verze *programu SGen.exe.* Tato vlastnost se používá pouze pro rozhraní .NET Framework.|
| SgenuseProxyTypy | Logická hodnota, která označuje, zda mají být typy proxy generovány souborem *SGen.exe*. To platí pouze v případě, že je funkce *GenerateSerializationAssemblies* nastavena na zapnuto a pouze pro rozhraní .NET Framework.<br /><br /> Cíl SGen používá tuto vlastnost k nastavení příznaku UseProxyTypes. Tato vlastnost výchozí true a neexistuje žádné uI to změnit. Chcete-li generovat sestavení serializace pro typy jiných než webservice, přidejte tuto vlastnost do souboru projektu a nastavte ji na hodnotu false před importem *cílů Microsoft.Common.Targets* nebo *C#/VB.targets*. |
| StartupObject | Určuje třídu nebo modul, který obsahuje metodu Main nebo proceduru Sub Main. Tato vlastnost je `/main` ekvivalentní přepínač kompilátoru. |
| Verze subsystému | Určuje minimální verzi subsystému, kterou může generovaný spustitelný soubor použít. Tato vlastnost je `/subsystemversion` ekvivalentní přepínač kompilátoru. Informace o výchozí hodnotě této vlastnosti naleznete v tématu [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) nebo [/subsystemversion (Možnosti kompilátoru Jazyka C#).](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option) |
| TargetCompactFramework | Verze rozhraní .NET Compact Framework, která je vyžadována ke spuštění vytvářené aplikace. Zadání tohoto umožňuje odkazovat na určité rozhraní sestavení, které nemusí být možné odkazovat jinak. |
| Cílová verze Framework | Verze rozhraní .NET Framework, která je vyžadována ke spuštění aplikace, kterou vytváříte. Zadání tohoto umožňuje odkazovat na určité rozhraní sestavení, které nemusí být možné odkazovat jinak. |
| TreatWarningsAsChyby | Logický parametr, který, `true`pokud , způsobí, že všechna upozornění, které mají být považovány za chyby. Tento parametr je `/nowarn` ekvivalentní přepínači kompilátoru. |
| UseHostCompilerIfAvailable | Logický parametr, který, `true`pokud , způsobí, že úloha sestavení použije objekt kompilátoru v procesu, pokud je k dispozici. Tento parametr používá pouze visual studio. |
| Utf8Výstup | Logický parametr, který `true`pokud protokoluje výstup kompilátoru pomocí kódování UTF-8. Tento parametr je `/utf8Output` ekvivalentní přepínači kompilátoru. |
| Cesta VbcToolPath | Volitelná cesta, která označuje jiné umístění pro *vbc.exe* při přepsání aktuální verze *programu vbc.exe.* |
| VbcVerbosita | Určuje podrobnost výstupu kompilátoru jazyka Visual Basic. Platné hodnoty jsou "Tichý", "Normální" (výchozí hodnota) nebo "Podrobné". |
| VisualStudioVersion | Určuje verzi sady Visual Studio, ve které by měl být tento projekt považován za spuštěný. Pokud tato vlastnost není zadán, MSBuild nastaví na přiměřenou výchozí hodnotu.<br /><br /> Tato vlastnost se používá v několika typech projektu k určení sady cílů, které se používají pro sestavení. Pokud `ToolsVersion` je pro projekt nastavena na `VisualStudioVersion` hodnotu 4.0 nebo vyšší, slouží k určení, kterou podsadu nástrojů chcete použít. Další informace naleznete v [tématu Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | Určuje seznam upozornění, která mají být považována za chyby. Tento parametr je `/warnaserror` ekvivalentní přepínači kompilátoru. |
| WarningsNotAsChyby | Určuje seznam upozornění, která nejsou považována za chyby. Tento parametr je `/warnaserror` ekvivalentní přepínači kompilátoru. |
| Win32Manifest | Název souboru manifestu, který by měl být vložen do konečného sestavení. Tento parametr je `/win32Manifest` ekvivalentní přepínači kompilátoru. |
| Win32Zdroj | Název souboru prostředku Win32, který má být vložen do konečného sestavení. Tento parametr je `/win32resource` ekvivalentní přepínači kompilátoru. |

## <a name="see-also"></a>Viz také

- [Běžné položky projektu MSBuild](../msbuild/common-msbuild-project-items.md)
