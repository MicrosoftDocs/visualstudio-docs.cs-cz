---
title: Správa odkazů v projektu
ms.date: 08/02/2019
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c55b0d3487eb18db33805b418882f157d55b1253
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183532"
---
# <a name="manage-references-in-a-project"></a>Správa odkazů v projektu

Před psaním kódu proti externí komponentě nebo připojené službě musí projekt nejprve obsahovat odkaz na něj. Odkaz je v podstatě záznam v souboru projektu, který obsahuje informace, které Visual Studio potřebuje k umístění komponenty nebo služby.

Chcete-li přidat odkaz, klikněte pravým tlačítkem myši na uzel **odkazy** nebo **závislosti** v **Průzkumník řešení** a vyberte možnost **Přidat odkaz**. Můžete také kliknout pravým tlačítkem myši na uzel projektu a vybrat možnost **Přidat**  >  **odkaz**. Další informace najdete v tématu [Postupy: Přidání nebo odebrání odkazů](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Přidat odkaz v jazyce Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png)

Můžete přidat odkaz na následující typy komponent a služeb:

- .NET – knihovny tříd nebo sestavení

- Aplikace pro UPW

- COM – součásti

- Další sestavení nebo knihovny tříd projektů ve stejném řešení

- Sdílené projekty

- webové služby XML

## <a name="uwp-app-references"></a>Odkazy na aplikace UWP

### <a name="project-references"></a>Odkazy na projekty

Projekty Univerzální platforma Windows (UWP) mohou vytvářet odkazy na jiné projekty UWP v řešení nebo pro Windows 8.1 projektů nebo binárních souborů za předpokladu, že tyto projekty nepoužívají rozhraní API, která se už nepoužívají ve Windows 10. Další informace najdete v tématu [Přesun z prostředí Windows Runtime 8 na UWP](/windows/uwp/porting/w8x-to-uwp-root).

Pokud se rozhodnete změnit cílení Windows 8.1 projektů na Windows 10, přečtěte si téma [port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Odkazy na sadu SDK rozšíření

Aplikace Visual Basic, C#, C++ a JavaScriptu Univerzální platforma Windows (UWP) mohou odkazovat na rozšíření sady SDK, které cílí na Windows 8.1, pokud tato rozšíření sady SDK nepoužívají rozhraní API, která se již nepoužívá ve Windows 10. Podívejte se na web dodavatele rozšíření SDK a zjistěte, jestli na něj můžou odkazovat aplikace pro UWP.

Pokud zjistíte, že sada SDK rozšíření, na kterou odkazuje vaše aplikace, není podporovaná, musíte provést následující kroky:

1. Podívejte se na název projektu, který způsobuje chybu. Platforma, na kterou váš projekt cílí, je uvedena v závorkách vedle názvu projektu. Například **MyProjectName (Windows 8.1)** znamená, že váš projekt **MyProjectName** je cílen na verzi platformy Windows 8.1.

1. Přejít na web dodavatele, který vlastní nepodporovanou sadu SDK, a nainstalovat verzi sady SDK rozšíření se závislostmi, které jsou kompatibilní s verzí platformy, na kterou váš projekt cílí.

    > [!NOTE]
    > Jedním ze způsobů, jak zjistit, jestli sada rozšíření SDK má závislosti na jiných sadách SDK rozšíření, je vyhledána v **nástroji Správce odkazů**. Restartujte Visual Studio, vytvořte nový projekt aplikace v C# pro UWP a pak klikněte pravým tlačítkem na projekt a zvolte **Přidat odkaz**. Klikněte na kartu **Windows** , pak na dílčí kartu **rozšíření** a vyberte sadu SDK rozšíření. Podívejte se do pravého podokna ve **Správci odkazů**. Pokud mají závislosti, budou uvedeny zde.

    > [!IMPORTANT]
    > Pokud projekt cílí na Windows 10 a sada rozšíření SDK nainstalovaná v předchozím kroku má závislost na balíčku Microsoft Visual C++ Runtime, verze Microsoft Visual C++ balíčku modulu runtime, která je kompatibilní s Windows 10 je v 14.0 a je nainstalovaná se sadou Visual Studio.

1. Pokud sada rozšíření SDK, kterou jste nainstalovali v předchozím kroku, má závislosti na dalších rozšířeních SDK, navštivte weby dodavatelů, kteří závislosti vlastní, a nainstalujte verze těchto závislostí, které jsou kompatibilní s verzí platformy, na kterou váš projekt cílí.

1. Restartujte Visual Studio a otevřete svoji aplikaci.

1. Klikněte pravým tlačítkem myši na uzel **odkazy** nebo **závislosti** v projektu, který způsobil chybu, a vyberte možnost **Přidat odkaz**.

1. Klikněte na kartu **Windows** a potom na dílčí kartu **rozšíření** a potom zrušte zaškrtnutí políček pro staré sady SDK rozšíření a zaškrtněte políčka pro nové sady SDK rozšíření. Klikněte na **OK**.

## <a name="add-a-reference-at-design-time"></a>Přidat odkaz v době návrhu

Když vytvoříte odkaz na sestavení v projektu, Visual Studio vyhledá sestavení v následujících umístěních:

- Aktuální adresář projektu. (Tato sestavení můžete najít pomocí karty **Procházet** .)

- Další adresáře projektu ve stejném řešení. (Tato sestavení můžete najít na kartě **projekty** .)

> [!NOTE]
> - Všechny projekty obsahují implicitní odkaz na **mscorlib**.
> - Všechny projekty obsahují implicitní odkaz na `System.Core` , i když `System.Core` je odebrán ze seznamu odkazů.
> - Visual Basic projekty obsahují implicitní odkaz na <xref:Microsoft.VisualBasic> .

## <a name="references-to-shared-components-at-run-time"></a>Odkazy na sdílené součásti za běhu

V době běhu musí být komponenty buď ve výstupní cestě projektu, nebo v globální mezipaměti sestavení (GAC). Pokud projekt obsahuje odkaz na objekt, který není v jednom z těchto umístění, je nutné zkopírovat odkaz na výstupní cestu projektu při sestavování projektu. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A>Vlastnost označuje, zda má být tato kopie vytvořena. Pokud je hodnota **true**, odkaz je zkopírován do adresáře projektu při sestavování projektu. Pokud je hodnota **false**, odkaz není zkopírován.

Pokud nasadíte aplikaci, která obsahuje odkaz na vlastní komponentu registrovanou v globální mezipaměti sestavení (GAC), komponenta nebude nasazena s aplikací bez ohledu na <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> nastavení. V dřívějších verzích sady Visual Studio bylo možné nastavit <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> vlastnost na odkaz, aby bylo zajištěno, že bylo sestavení nasazeno. Nyní je třeba ručně přidat sestavení do složky \Bin. Tím se veškerý vlastní kód uloží do kontroly a snižuje riziko publikování vlastního kódu, se kterým nejste obeznámeni.

Ve výchozím nastavení <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> je vlastnost nastavena na **hodnotu false** , je-li sestavení nebo komponenta v globální mezipaměti sestavení (GAC) nebo je součástí rozhraní. V opačném případě je hodnota nastavena na **true**. Odkazy z projektu na projekt jsou vždy nastaveny na **hodnotu true**.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-net"></a>Odkaz na projekt nebo sestavení, které cílí na jinou verzi rozhraní .NET

Můžete vytvářet aplikace, které odkazují na projekty nebo sestavení, které cílí na jinou verzi rozhraní .NET. Můžete například vytvořit aplikaci, která cílí na .NET Framework 4,6, která odkazuje na sestavení, které cílí na .NET Framework 4,5. Vytvoříte-li projekt, který se zaměřuje na starší verzi rozhraní .NET, nemůžete v tomto projektu nastavit odkaz na projekt nebo sestavení, které cílí na novější verzi.

Další informace najdete v tématu [Přehled cílení na rozhraní](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Odkazy z projektu na projekt

Odkazy z projektu na projekt jsou odkazy na projekty obsahující sestavení; odkazy na projekt můžete přidat pomocí karty **projekty** v dialogovém okně Správce odkazů. Visual Studio může najít sestavení, pokud je předána cesta k projektu.

Pokud máte projekt, který vytváří sestavení, měli byste odkazovat na projekt a nepoužívat odkaz na soubor (viz níže). Výhodou odkazu typu projekt-projekt je, že vytvoří závislost mezi projekty v systému sestavení. Závislý projekt bude sestaven, pokud byl od posledního vytvoření odkazujícího projektu změněn. Odkaz na soubor nevytváří závislost sestavení, takže je možné sestavit odkazující projekt bez sestavení závislého projektu a odkaz může být zastaralý. (To znamená, že projekt může odkazovat na dříve sestavenou verzi projektu.) To může mít za následek, že v adresáři *bin* je vyžadováno několik verzí jediné knihovny DLL, což není možné. Když dojde ke konfliktu, zobrazí se zpráva, například "Upozornění: závislost ' souboru ' v projektu ' Project ' nelze zkopírovat do běhového adresáře, protože by přepsala odkaz ' file '. Další informace najdete v tématu [řešení potíží s poškozenými odkazy](../ide/troubleshooting-broken-references.md) a [Postupy: vytvoření a odebrání závislostí projektu](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Odkaz na soubor namísto odkazu projekt-projekt je vytvořen, pokud je cílová verze .NET Framework jednoho projektu verze 4,5 a cílová verze druhého projektu je verze 2, 3, 3,5 nebo 4,0.

## <a name="shared-project-references"></a>Odkazy na sdílené projekty

Na rozdíl od většiny ostatních typů projektu, *sdílený projekt* nemá žádný binární výstup. Místo toho je kód zkompilován do každého projektu, který na něj odkazuje. [Sdílené projekty](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) umožňují psát společný kód, na který odkazuje několik různých aplikačních projektů. Kód je kompilován jako součást každého odkazujícího projektu a může obsahovat direktivy kompilátoru, které pomohou integrovat funkce specifické pro platformu do základu sdíleného kódu. Přidejte odkaz na sdílený projekt na kartě **sdílené projekty** v dialogovém okně Správce odkazů.

## <a name="file-references"></a>Odkazy na soubory

Odkazy na soubory jsou přímé odkazy na sestavení mimo kontext projektu sady Visual Studio. Vytvoříte je pomocí karty **Procházet** v dialogovém okně Správce odkazů. Odkaz na soubor použijte, pokud máte pouze sestavení nebo komponentu, a ne projekt, který jej vytvoří jako výstup.

## <a name="see-also"></a>Viz také

- [Řešení problémů s poškozenými odkazy](../ide/troubleshooting-broken-references.md)
- [Postupy: Přidání nebo odebrání odkazů](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
