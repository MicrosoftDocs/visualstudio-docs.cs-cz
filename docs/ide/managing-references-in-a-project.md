---
title: Správa odkazů v projektu
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e772f4d861e4b16499ad9be9d7c814320e1a14f9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950943"
---
# <a name="manage-references-in-a-project"></a>Správa odkazů v projektu

Než psát kód pro místní externí komponenta nebo připojené služby, projektu musí nejprve obsahovat odkaz na jeho. Odkaz je v podstatě položku v souboru projektu, který obsahuje informace, že Visual Studio se musí vyhledat daná komponenta nebo služba.

Přidat odkaz, klikněte pravým tlačítkem na **odkazy** nebo **závislosti** uzlu v **Průzkumníku řešení** a zvolte **přidat odkaz na**. Můžete také kliknout pravým tlačítkem na uzel projektu a vyberte **přidat** > **odkaz**. Další informace najdete v tématu [postupy: Přidání nebo odebrání odkazů](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Přidat odkaz v jazyce Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png)

Můžete přidat odkaz na následující typy součástmi a službami:

- Knihovna tříd rozhraní .NET framework nebo sestavení

- Aplikace UWP

- COM – součásti

- Další sestavení nebo knihovny tříd projektů ve stejném řešení

- webové služby XML

## <a name="uwp-app-references"></a>Odkazy na aplikace UWP

### <a name="project-references"></a>Odkazy na projekt

Projekty pro Universal Windows Platform (UWP) můžete vytvořit odkazy na další UWP projekty v řešení, nebo projekty Windows 8.1 nebo binární soubory, za předpokladu, že tyto projekty nepoužívají rozhraní API, která jsou zastaralé v systému Windows 10. Další informace najdete v tématu [přesunutí ze systému Windows 8 Runtime UWP](/windows/uwp/porting/w8x-to-uwp-root).

Pokud zvolíte možnost změnit cílový projekty Windows 8.1 na Windows 10, najdete v části [Port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Reference na rozšíření sady SDK

Aplikace Visual Basic, C#, C++ a JavaScript univerzální platformu Windows (UWP) můžete odkazovat rozšíření sady SDK cílených Windows 8.1, tak dlouho, dokud tyto rozšíření sady SDK se nedoporučuje používat rozhraní API, která jsou zastaralé v systému Windows 10. Zkontrolujte, zda webu dodavatele rozšíření sady SDK a zjistěte, zda může být odkazován aplikace UWP.

Pokud zjistíte, že rozšíření sady SDK, se na ně odkazovat aplikace není podporována, pak je třeba provést následující kroky:

1. Podívejte se na název projektu, který je příčinou chyby. Platformy, na které je cílem vašeho projektu je uvedeno v závorkách vedle názvu projektu. Například **(Windows 8.1) s názvem MyProjectName** znamená, že váš projekt **s názvem MyProjectName** je cílení na platformy verzi Windows 8.1.

1. Přejděte na webu dodavatele, který vlastní nepodporované Extension SDK a nainstalujte verzi sady SDK rozšíření se závislostmi, které jsou kompatibilní s verzí platformy, na které cílí projektu.

    > [!NOTE]
    > Je možné zjistit, jestli má závislosti na dalších sadách SDK rozšíření Extension SDK podle **správce odkazů**. Restartujte Visual Studio, vytvořte nový projekt aplikace UPW C# a potom klikněte pravým tlačítkem na projekt a zvolte **přidat odkaz na**. Přejděte na **Windows** kartě, pak se **rozšíření** dílčí karty a vyberte rozšíření sady SDK. Podívejte se na v pravém podokně **správce odkazů**. Pokud má závislosti, budou uvedené existuje.

    > [!IMPORTANT]
    > Pokud váš projekt je cílení na Windows 10 a sady SDK rozšíření nainstalovaná v předchozím kroku má závislost na balíček Microsoft Visual C++ Runtime, v14.0 na verzi Microsoft Visual C++ Runtime balíčku, který je kompatibilní s Windows 10 a je nainstalován pomocí sady Visual Studio.

1. Pokud sada SDK rozšíření jste nainstalovali v předchozím kroku má závislosti na dalších sadách SDK rozšíření, přejděte do lokalit dodavatelů, kteří vlastní závislosti a nainstalujte verze tyto závislosti, které jsou kompatibilní s verzí platformy, na které je váš projekt cílení na.

1. Restartujte Visual Studio a otevřete v aplikaci.

1. Klikněte pravým tlačítkem na **odkazy** nebo **závislosti** uzlu v projektu, který způsobil chybu a zvolte **přidat odkaz na**.

1. Klikněte na tlačítko **Windows** kartu a potom **rozšíření** dílčí, poté zrušte zaškrtnutí políček pro původní sady SDK rozšíření a zkontrolujte políček pro nové sady SDK rozšíření. Click **OK**.

## <a name="add-a-reference-at-design-time"></a>Přidat odkaz v době návrhu

Když do projektu odkaz na sestavení, Visual Studio vyhledává sestavení v následujících umístěních:

- Aktuální adresář projektu. (Tyto sestavení můžete najít pomocí **Procházet** karta.)

- Další adresáře projektu ve stejném řešení. (Tyto sestavení můžete najít na **projekty** karta.)

> [!NOTE]
> - Všechny projekty obsahují implicitní odkaz na **mscorlib**.
> - Všechny projekty obsahují implicitní odkaz na `System.Core`i v případě `System.Core` se odebere ze seznamu odkazů.
> - Projekty Visual Basic obsahují implicitní odkaz na <xref:Microsoft.VisualBasic>.

## <a name="references-to-shared-components-at-run-time"></a>Odkazy na sdílené komponenty v době běhu

V době běhu součásti musí být v cestě výstupu projektu nebo v globální mezipaměti sestavení (GAC). Pokud projekt obsahuje odkaz na objekt, který není v jednom z těchto umístění, je nutné zkopírovat odkaz na cestu výstupního projektu při sestavování projektu. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> Vlastnost určuje, zda tato kopie má být provedena. Pokud je hodnota **True**, odkaz je zkopírován do adresáře projektu při sestavování projektu. Pokud je hodnota **False**, odkaz se nezkopíruje.

Pokud nasadíte aplikaci, která obsahuje odkaz na komponentu vlastní, které je registrované v mezipaměti GAC, součást nebude nasazen s aplikací, bez ohledu na to <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> nastavení. V dřívějších verzích sady Visual Studio, můžete nastavit <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> vlastnost na odkaz k zajištění, že byla nasazena sestavení. Nyní je třeba ručně přidat sestavení do složky \Bin. To umístí všechny vlastní kód pod kontrolu, snižuje riziko publikování vlastní kód, pomocí kterého nejste obeznámeni.

Ve výchozím nastavení <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> je nastavena na **False** Pokud sestavení nebo součást je v globální mezipaměti sestavení nebo komponentu prostředí. Jinak je hodnota nastavená **True**. Odkazy na projekt na projekt jsou vždy nastavená **True**.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odkaz na projekt nebo sestavení, které jinou verzi rozhraní .NET Framework

Můžete vytvořit aplikace, které odkazují na projekty nebo sestavení, které jinou verzi rozhraní .NET Framework. Například můžete vytvořit aplikace s cílem rozhraní .NET Framework 4.6, které odkazuje na sestavení, která je cílena rozhraní .NET Framework 4.5. Pokud vytvoříte projekt, který se zaměřuje na starší verzi rozhraní .NET Framework, nemůžete nastavit odkaz v tomto projektu projekt nebo sestavení, která je cílena na novější verzi.

Další informace najdete v tématu [přehled cílení na více](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Projekt do odkazů projektu

Odkazy na projekt na projekt jsou odkazy na projekty, které obsahují sestavení; můžete vytvořit pomocí **projektu** kartě. Visual Studio můžete najít sestavení při zadána cesta k projektu.

Až budete mít na projekt, který vytváří sestavení, by měla odkazovat na projekt a nechcete použít odkaz na soubor (viz níže). Výhodou odkaz na projekt na projekt je, že vytvoří závislost mezi projekty v systému sestavení. Závislé projektu budou vytvořeny, pokud se změnil od posledního odkazujícího projektu. Odkaz na soubor nevytvoří závislost sestavení, takže je možné vytvořit odkazující projekt bez vytváření závislého projektu a odkaz se může stát zastaralé. (To znamená, projekt může odkazovat na dřívější sestavené verze projektu.) To může způsobit v několika verzích jeden soubor DLL v nich vyžaduje *bin* adresáři, který není možné. Když dojde k tomuto konfliktu, zobrazí se zpráva, jako "Upozornění: závislost 'file' v projektu 'project' nelze zkopírovat do běhového adresáře, protože by přepsala odkaz 'file.'". Další informace najdete v tématu [Poradce při potížích přerušený odkazy](../ide/troubleshooting-broken-references.md) a [postupy: vytvoření a odebrání závislostí projektu](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Odkaz na soubor místo odkaz na projekt na projekt se vytvoří, pokud je cílová verze rozhraní .NET Framework projektu jeden verze 4.5 a cílovou verzi sady jiný projekt je verze 2, 3, 3.5 nebo 4.0.

## <a name="file-references"></a>Odkazy na soubory

Odkazy na soubory jsou přímé odkazy na sestavení mimo kontext projekt sady Visual Studio. Můžete vytvořit pomocí **Procházet** kartě **správce odkazů**. Použijte odkaz na soubor, pokud máte právě sestavení nebo součásti a ne na projekt, který vytvoří jako výstup.

## <a name="see-also"></a>Viz také

- [Řešení potíží s poškozenými odkazy](../ide/troubleshooting-broken-references.md)
- [Postupy: Přidání nebo odebrání odkazů](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
