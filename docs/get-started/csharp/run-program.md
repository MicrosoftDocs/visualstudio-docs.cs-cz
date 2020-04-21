---
title: Jak spustit program (C#)
description: Průvodce pro začátečníky o spuštění programu Jazyka C# v sadě Visual Studio.
ms.custom: get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ee28bde6de10006ccfdc5175cca629ad9d1590d0
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649636"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Postup: Spuštění programu Jazyka C# v sadě Visual Studio

Co je třeba udělat pro spuštění programu, závisí na tom, od čeho začínáte, jaký typ programu, aplikace nebo služby je a zda jej chcete spustit pod ladicím programem nebo ne. V nejjednodušším případě, když máte projekt otevřený v sadě Visual Studio, sestavte a spusťte stisknutím **kláves Ctrl**+**F5** ( Start bez**ladění**) nebo **F5** (**Začněte laděním**) nebo stiskněte zelenou šipku (**Tlačítko Start**) na hlavním panelu nástrojů sady Visual Studio.

![Snímek obrazovky s tlačítkem Start](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Počínaje projektem

Pokud máte c# projekt (*.csproj* soubor), pak jej můžete spustit, pokud se jedná o spustitelný program. Pokud projekt obsahuje soubor Jazyka `Main` C# s metodou a jeho výstup je spustitelný soubor (EXE), pak s největší pravděpodobností bude spuštěn, pokud se úspěšně vytvoří.

Pokud již máte kód pro váš program v projektu v sadě Visual Studio, otevřete projekt. Chcete-li projekt otevřít, poklepejte nebo klepněte na *soubor .csproj* z Průzkumníka souborů Windows nebo z aplikace Visual Studio, zvolte **Otevřít projekt**, vyhledejte soubor projektu (*csproj*) a zvolte soubor projektu.

Po načtení projektů v sadě Visual Studio spusťte program stisknutím **klávesCtrl**+**F5** **(Start without debugging)** nebo pomocí zeleného tlačítka **Start** na panelu nástrojů sady Visual Studio.  Pokud existuje více projektů, musí `Main` být jako projekt při spuštění nastaven a toto s metodou. Chcete-li nastavit projekt po spuštění, klepněte pravým tlačítkem myši na uzel projektu a zvolte **Nastavit jako spouštěcí projekt**.

![Nastavení projektu spuštění](media/set-as-startup-project.png)

Visual Studio se pokusí vytvořit a spustit projekt.  Pokud jsou chyby sestavení, zobrazí se výstup sestavení v okně **Výstup** a chyby v okně **Seznam chyb.**

Pokud sestavení úspěšné, aplikace běží způsobem, který je vhodný pro typ projektu. Konzolové aplikace běží v okně terminálu, aplikace klasické pracovní plochy windows se spouštějí v novém okně, webové aplikace se spouštějí v prohlížeči (hostované službou IIS Express) a tak dále.

## <a name="starting-from-code"></a>Počínaje kódem

Pokud začínáte se seznamem kódu, souborem kódu nebo malým počtem souborů, nejprve se ujistěte, že kód, který chcete spustit, pochází z důvěryhodného zdroje a je spustitelný program. Pokud má `Main` metodu, je pravděpodobně určena jako spustitelný program, který můžete použít šablonu konzolové aplikace k vytvoření projektu pro práci s ní v sadě Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Výpis kódu pro jeden soubor

Spusťte Visual Studio, otevřete prázdný projekt konzoly C#, vyberte veškerý kód v souboru .cs, který je již v projektu, a odstraňte ho. Potom vložte obsah kódu do souboru .cs. Při vložení kódu přepište nebo odstraňte kód, který tam byl předtím. Přejmenujte soubor tak, aby odpovídal původnímu kódu.

### <a name="code-listings-for-a-few-files"></a>Výpisy kódu pro několik souborů

Spusťte Visual Studio, otevřete prázdný projekt konzoly C#, vyberte veškerý kód v souboru .cs, který je již v projektu, a odstraňte ho. Potom vložte obsah prvního souboru kódu do souboru .cs. Přejmenujte soubor tak, aby odpovídal původnímu kódu. 

U druhého souboru klikněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení,** otevřete místní nabídku projektu a zvolte **Přidat > existující položku** (nebo použijte kombinaci kláves **Shift**+**Alt**+**A**) a vyberte soubory kódu.

### <a name="multiple-files-on-disk"></a>Více souborů na disku

1. Vytvořte nový projekt příslušného typu (pokud si nejste jisti, použijte **konzolovou aplikaci** C#).

2. Klikněte pravým tlačítkem myši na uzel projektu, se **Přidat** > **existující položku** vyberte soubory a importujte je do projektu.  

### <a name="starting-from-a-folder"></a>Spuštění ze složky

Při práci se složkou s mnoha soubory nejprve zjistěte, zda existuje projekt nebo řešení.  Pokud byl program vytvořen pomocí sady Visual Studio, měli byste najít soubor projektu nebo soubor řešení. Vyhledejte soubory s příponou *.csproj* nebo .sln a v Průzkumníkovi souborů windows, poklepáním na jeden z nich je otevřete v sadě Visual Studio. Viz [Spuštění z řešení nebo projektu sady Visual Studio](#starting-from-a-project).

Pokud nemáte soubor projektu, například pokud byl kód vyvinut v jiném vývojovém prostředí, otevřete složku nejvyšší úrovně pomocí metody **Otevřít složku** v sadě Visual Studio. Viz [Vývoj kódu bez projektů nebo řešení](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>Počínaje úložištěm GitHub nebo Azure DevOps

Pokud kód, který chcete spustit, je v GitHubu nebo v úložišti Azure DevOps, můžete projekt otevřít pomocí Visual Studia přímo z úložiště. Viz [Otevření projektu z repo](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Spuštění programu

Program spustíte stisknutím zelené šipky **(tlačítko Start)** na hlavním panelu nástrojů sady Visual Studio nebo stisknutím **klávesY F5** nebo **Ctrl**+**F5.** Při použití tlačítka **Start** se spustí pod ladicím programem.  Visual Studio se pokusí vytvořit kód v projektu a spustit jej.  Pokud se to podaří, skvělé! Ale pokud ne, pokračovat ve čtení pro některé nápady, jak se dostat do stavět úspěšně.

## <a name="troubleshooting"></a>Poradce při potížích

Váš kód může mít chyby, ale pokud je kód správný, ale závisí pouze na některých jiných sestaveních nebo balíčcích NuGet nebo byl napsán tak, aby cílit na jinou verzi rozhraní .NET, můžete jej snadno opravit.

### <a name="add-references"></a>Přidání odkazů

Chcete-li vytvořit správně, kód musí být správné a mít správné odkazy nastaveny na knihovny nebo jiné závislosti. Můžete se podívat na červené klikaté řádky a na **seznamu chyb,** abyste zjistili, zda má program nějaké chyby, a to ještě předtím, než jej zkompilujete a spustíte. Pokud se vám zobrazují chyby související s nevyřešenými názvy, budete pravděpodobně muset přidat odkaz nebo direktivu using nebo obojí. Pokud kód odkazuje na všechna sestavení nebo balíčky NuGet, je třeba přidat tyto odkazy v projektu.

Visual Studio se pokusí pomoci identifikovat chybějící odkazy. Pokud není název vyřešen, zobrazí se v editoru ikona žárovky. Pokud kliknete na žárovku, zobrazí se několik návrhů, jak problém vyřešit. Opravy mohou být:

- přidat direktivu using
- přidat odkaz na sestavu, nebo
- nainstalujte balíček NuGet.

#### <a name="missing-using-directive"></a>Chybí using směrnice

Například na následující obrazovce můžete přidat `using System;` na začátek souboru kódu přeložit nevyřešený název `Console`:

![Snímek obrazovky s žárovkou pro přidání direktivy using](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Chybí odkaz na sestavení

Odkazy .NET mohou být ve formě sestavení nebo balíčků NuGet. Obvykle pokud najdete zdrojový kód, vydavatel nebo autor vysvětlí, jaké sestavení jsou požadovány a jaké balíčky kód závisí na. Chcete-li přidat odkaz na projekt ručně, klepněte pravým tlačítkem myši na uzel **Reference** v **Průzkumníku řešení**, zvolte **Přidat odkaz**a vyhledejte požadované sestavení.

![Snímek obrazovky s nabídkou Přidat odkaz](media/add-reference.png)

Sestavení můžete najít a přidat odkazy podle pokynů v [části Přidat nebo odebrat odkazy pomocí správce odkazů](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="missing-nuget-package"></a>Chybějící balíček NuGet

Pokud Visual Studio zjistí chybějící balíček NuGet, zobrazí se žárovka a poskytuje možnost ji nainstalovat:

![Snímek obrazovky s žárovkou pro instalaci balíčku](media/lightbulb-add-package.png)

Pokud se tím problém nevyřeší a Visual Studio nemůže balíček najít, zkuste ho vyhledat online. Viz [Instalace a použití balíčku NuGet v sadě Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Použití správné verze rozhraní .NET

Vzhledem k tomu, že různé verze rozhraní .NET Framework mají určitý stupeň zpětné kompatibility, novější framework může spustit kód napsaný pro starší rozhraní bez jakýchkoli úprav. Někdy však musíte cílit na konkrétní rámec. Možná budete muset nainstalovat určitou verzi rozhraní .NET Framework nebo .NET Core, pokud ještě není nainstalována. Viz [Úprava sady Visual Studio](../../install/modify-visual-studio.md).

Pokud chcete změnit cílový rámec, přečtěte si informace [o změně cílového rozhraní](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Další informace naleznete [v tématu Poradce při potížích s chybami cílení rozhraní .NET Framework](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Další kroky

Prozkoumejte vývojové prostředí sady Visual Studio přečtením [vítání ide sady Visual Studio](../visual-studio-ide.md).

## <a name="see-also"></a>Viz také

[Vytvoření první aplikace v C#](tutorial-console.md)
