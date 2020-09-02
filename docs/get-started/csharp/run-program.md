---
title: Jak spustit program (C#)
description: Příručka pro začátečníky, jak spustit program v jazyce C# v aplikaci Visual Studio.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649636"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Postupy: spuštění programu v jazyce C# v aplikaci Visual Studio

To, co potřebujete ke spuštění programu, závisí na tom, co začínáte, jaký typ programu, aplikace nebo služby je a zda ho chcete spustit pod ladicím programem. V nejjednodušším případě, když máte projekt otevřený v sadě Visual Studio, sestavte ho a spusťte stisknutím klávesy **CTRL** + **F5** (**Spustit bez ladění**) nebo **F5** (**Spustit s laděním**) nebo stiskněte zelenou šipku (**tlačítko Start**) na hlavním panelu nástrojů sady Visual Studio.

![Snímek obrazovky se zobrazeným tlačítkem Start](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Spuštění z projektu

Pokud máte projekt C# (soubor *. csproj* ), můžete ho spustit, pokud se jedná o program spustitelný. Pokud projekt obsahuje soubor C# s `Main` metodou a jeho výstupem je spustitelný soubor (exe), je nejpravděpodobnější, že se spustí, pokud se úspěšně sestaví.

Pokud již máte kód pro svůj program v projektu v aplikaci Visual Studio, otevřete projekt. Chcete-li projekt otevřít, dvakrát klikněte nebo klepněte na soubor *. csproj* z Průzkumníka souborů systému Windows nebo ze sady Visual Studio, vyberte možnost **Otevřít projekt**, vyhledejte soubor projektu (*. csproj*) a vyberte soubor projektu.

Po načtení projektů v sadě Visual Studio stiskněte klávesu **CTRL** + **F5** (**Spustit bez ladění**) nebo použijte zelené tlačítko **Start** na panelu nástrojů sady Visual Studio ke spuštění programu.  Pokud existuje více projektů, `Main` musí být metoda s metodou nastavena jako spouštěný projekt. Chcete-li nastavit projekt po spuštění, klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **nastavit jako spouštěný projekt**.

![Nastavení spouštěného projektu](media/set-as-startup-project.png)

Visual Studio se pokusí sestavit a spustit váš projekt.  Pokud dojde k chybám sestavení, zobrazí se výstup sestavení v okně **výstup** a chyby v okně **Seznam chyb** .

Pokud je sestavení úspěšné, aplikace bude spuštěna způsobem, který je vhodný pro typ projektu. Konzolové aplikace běží v okně terminálu. aplikace pro desktopové aplikace pro Windows se spouštějí v novém okně. Web Apps se spouští v prohlížeči (hostovaném IIS Express), a tak dále.

## <a name="starting-from-code"></a>Počínaje kódem

Pokud začínáte ze seznamu kódu, souboru s kódem nebo malého počtu souborů, nejprve se ujistěte, že kód, který chcete spustit, pochází z důvěryhodného zdroje a je spustitelný program. Pokud má `Main` metodu, je pravděpodobně určena jako spustitelný program, který můžete použít k vytvoření projektu pro práci v aplikaci Visual Studio pomocí šablony Konzolová aplikace.

### <a name="code-listing-for-a-single-file"></a>Výpis kódu pro jeden soubor

Spusťte Visual Studio, otevřete prázdný projekt konzoly C#, vyberte veškerý kód v souboru. cs, který je v projektu, a odstraňte ho. Pak vložte obsah kódu do souboru. cs. Když kód vložíte, přepište nebo odstraňte kód, který existoval dříve. Přejmenujte soubor tak, aby odpovídal původnímu kódu.

### <a name="code-listings-for-a-few-files"></a>Výpisy kódu pro několik souborů

Spusťte Visual Studio, otevřete prázdný projekt konzoly C#, vyberte veškerý kód v souboru. cs, který je v projektu, a odstraňte ho. Pak vložte obsah prvního souboru s kódem do souboru. cs. Přejmenujte soubor tak, aby odpovídal původnímu kódu. 

Pro druhý soubor kliknutím pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** otevřete místní nabídku pro projekt a zvolte možnost **Přidat > existující položku** (nebo použijte kombinaci kláves **SHIFT** + **+** + **a**) a vyberte soubory kódu.

### <a name="multiple-files-on-disk"></a>Více souborů na disku

1. Vytvoří nový projekt příslušného typu (Pokud si nejste jistí, použijte **konzolovou aplikaci** v jazyce C#).

2. Po kliknutí pravým tlačítkem myši na uzel projektu se zobrazí položka **Přidat**  >  **existující položku** pro výběr souborů a import do projektu.  

### <a name="starting-from-a-folder"></a>Spuštění ze složky

Když pracujete se složkou mnoha souborů, nejprve se podívejte, jestli existuje projekt nebo řešení.  Pokud byl program vytvořen pomocí sady Visual Studio, měli byste najít soubor projektu nebo soubor řešení. Vyhledejte soubory s příponou *. csproj* nebo s příponou. sln a v Průzkumníkovi souborů systému Windows dvakrát klikněte na jeden z nich a otevřete si je v aplikaci Visual Studio. Viz téma [zahájení z řešení nebo projektu sady Visual Studio](#starting-from-a-project).

Pokud nemáte soubor projektu, například pokud byl kód vyvinut v jiném vývojovém prostředí, otevřete složku nejvyšší úrovně pomocí metody **Open Folder** v aplikaci Visual Studio. Viz [vývoj kódu bez projektů nebo řešení](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>Od GitHubu nebo úložiště Azure DevOps

Pokud je kód, který chcete spustit, v GitHubu nebo v úložišti Azure DevOps, můžete k otevření projektu přímo z úložiště použít Visual Studio. Viz [Otevřít projekt z úložiště](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Spuštění programu

Chcete-li spustit program, stiskněte zelenou šipku (tlačítko**Start** ) na hlavním panelu nástrojů sady Visual Studio nebo stiskněte klávesu **F5** nebo **CTRL** + **F5** a program spusťte. Když použijete tlačítko **Start** , spustí se v ladicím programu.  Visual Studio se pokusí sestavit kód v projektu a spustit ho.  Pokud to bude úspěšné, Skvělé! Ale pokud ne, pokračujte v čtení některých nápadů, jak je získat na úspěšné sestavení.

## <a name="troubleshooting"></a>Řešení potíží

Váš kód může mít chyby, ale pokud je kód správný, ale závisí jenom na některých dalších sestaveních nebo balíčcích NuGet, nebo jestli byl zapsaný na jinou verzi rozhraní .NET, možná ho budete moct snadno opravit.

### <a name="add-references"></a>Přidat odkazy

Aby bylo možné správně sestavit kód, musí být kód správný a mít správné odkazy nastaveny na knihovny nebo jiné závislosti. Můžete se podívat na červené vlnovky a na **Seznam chyb** a zjistit, jestli program obsahuje nějaké chyby, dokonce i před tím, než ho zkompilujete a spustíte. Pokud se zobrazují chyby týkající se nevyřešených názvů, pravděpodobně budete muset přidat odkaz nebo direktivu using nebo obojí. Pokud kód odkazuje na jakákoli sestavení nebo balíčky NuGet, je nutné přidat tyto odkazy do projektu.

Visual Studio se snaží vám poznat chybějící odkazy. Pokud je název nevyřešený, zobrazí se v editoru ikona žárovky. Pokud kliknete na žárovku, uvidíte některé návrhy, jak problém vyřešit. Opravy mohou být:

- Přidání direktivy using
- Přidejte odkaz na sestavení nebo
- Nainstalujte balíček NuGet.

#### <a name="missing-using-directive"></a>Chybějící Direktiva using

Například na následující obrazovce můžete přidat `using System;` na začátek souboru kódu k vyřešení nerozpoznaného názvu `Console` :

![Obrázek žárovky pro přidání direktivy using](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Chybějící odkaz na sestavení

Odkazy .NET můžou být ve formě sestavení nebo balíčků NuGet. Pokud například vyhledáte zdrojový kód, Vydavatel nebo autor vysvětlete, jaká sestavení jsou povinná a jaké balíčky závisí na kódu. Chcete-li přidat odkaz na projekt ručně, klikněte pravým tlačítkem myši na uzel **odkazy** v **Průzkumník řešení**, vyberte možnost **Přidat odkaz**a vyhledejte požadované sestavení.

![Snímek obrazovky nabídky Přidat odkaz](media/add-reference.png)

Můžete najít sestavení a přidat odkazy podle pokynů v tématu [Přidání nebo odebrání odkazů pomocí Správce odkazů](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="missing-nuget-package"></a>Chybějící balíček NuGet

Pokud Visual Studio zjistí chybějící balíček NuGet, zobrazí se žárovka a nabídne vám možnost je nainstalovat:

![Snímek žárovky pro instalaci balíčku](media/lightbulb-add-package.png)

Pokud se tím problém nevyřeší a sada Visual Studio nemůže balíček najít, zkuste ho vyhledat online. Viz [instalace a použití balíčku NuGet v aplikaci Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Použití správné verze .NET

Vzhledem k tomu, že různé verze .NET Framework mají určitou úroveň zpětné kompatibility, může novější rozhraní spustit kód napsaný pro starší verzi rozhraní bez jakýchkoli úprav. Někdy ale potřebujete cílit na konkrétní rámec. Je možné, že budete muset nainstalovat určitou verzi .NET Framework nebo .NET Core, pokud ještě není nainstalovaná. Viz [Změna sady Visual Studio](../../install/modify-visual-studio.md).

Chcete-li změnit cílovou architekturu, přečtěte si téma [Změna cílové architektury](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Další informace najdete v tématu [řešení potíží s chybami cílení .NET Framework](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Další kroky

Prozkoumejte vývojové prostředí sady Visual Studio tak, že si přečtete [Vítá vás Visual Studio IDE](../visual-studio-ide.md).

## <a name="see-also"></a>Viz také

[Vytvoření první aplikace jazyka C#](tutorial-console.md)
