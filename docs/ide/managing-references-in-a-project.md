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
ms.openlocfilehash: 9623e8ffb6a315851d26cd06defb62899e429f44
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591252"
---
# <a name="manage-references-in-a-project"></a>Správa odkazů v projektu

Před zápisem kódu proti externí součásti nebo připojené službě musí projekt nejprve obsahovat odkaz na něj. Odkaz je v podstatě položka v souboru projektu, který obsahuje informace, které Visual Studio potřebuje k vyhledání komponenty nebo služby.

Chcete-li přidat odkaz, klikněte pravým tlačítkem myši na uzel **Odkazy** nebo **závislosti** v **Průzkumníku řešení** a zvolte **Přidat odkaz**. Můžete také kliknout pravým tlačítkem myši na uzel projektu a vybrat **přidat** > **odkaz**. Další informace naleznete v [tématu Jak: Přidání nebo odebrání odkazů](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Přidání odkazu do aplikace Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png)

Můžete přidat odkaz na následující typy součástí a služeb:

- Knihovny nebo sestavení tříd .NET

- Aplikace pro UPW

- COM – součásti

- Jiná sestavení nebo knihovny tříd projektů ve stejném řešení

- Sdílené projekty

- webové služby XML

## <a name="uwp-app-references"></a>Odkazy na aplikace UPW

### <a name="project-references"></a>Odkazy na projekty

Projekty univerzální platformy Windows (UPW) můžete vytvořit odkazy na jiné projekty UPW v řešení nebo windows 8.1 projekty nebo binární soubory, za předpokladu, že tyto projekty nepoužívají api, které byly zastaralé v systému Windows 10. Další informace naleznete v tématu [Přesun z prostředí Windows Runtime 8 do UPW](/windows/uwp/porting/w8x-to-uwp-root).

Pokud se rozhodnete přecílit na projekty Windows 8.1 na Windows 10, přečtěte si informace [o portech, migraci a upgradu projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Odkazy na sady SDK rozšíření

Aplikace Visual Basic, C#, C++ a JavaScript Universal Windows Platform (UPW) můžou odkazovat na sady SDK rozšíření, které cílí na Windows 8.1, pokud tyto sady SDK rozšíření nepoužívají api, která byla v systému Windows 10 zastaralá. Zkontrolujte web dodavatele sady Extension SDK a zjistěte, zda na něj mohou odkazovat aplikace UPW.

Pokud zjistíte, že sada SDK rozšíření, na kterou vaše aplikace odkazuje, není podporovaná, musíte provést následující kroky:

1. Podívejte se na název projektu, který je příčinou chyby. Platforma, na kterou je projekt zaměřen, je zaznamenána v závorcích vedle názvu projektu. Například **MyProjectName (Windows 8.1)** znamená, že váš projekt **MyProjectName** je cílení verze platformy Windows 8.1.

1. Přejděte na web dodavatele, který vlastní nepodporovanou sadku SDK rozšíření, a nainstalujte verzi sady SDK rozšíření se závislostmi, které jsou kompatibilní s verzí platformy, na kterou projekt cílí.

    > [!NOTE]
    > Jedním ze způsobů, jak zjistit, zda sada SDK rozšíření obsahuje závislosti na jiných sadách SDK rozšíření, je vyhledáním ve **Správci odkazů**. Restartujte Visual Studio, vytvořte nový projekt aplikace C# UWP a potom klikněte pravým tlačítkem myši na projekt a zvolte **Přidat odkaz**. Přejděte na kartu **Windows,** potom na dílčí kartu **Rozšíření** a vyberte sadu SDK rozšíření. Podívejte se do pravého podokna ve **Správci odkazů**. Pokud má závislosti, budou uvedeny zde.

    > [!IMPORTANT]
    > Pokud váš projekt cílí na Windows 10 a sada SDK rozšíření nainstalovaná v předchozím kroku je závislá na runtime balíčku Microsoft Visual C++, verze balíčku Runtime Microsoft Visual C++, která je kompatibilní s Windows 10, je verze v14.0 a je nainstalovaná s visual studio.

1. Pokud sada SDK rozšíření nainstalovaná v předchozím kroku obsahuje závislosti na jiných sadách SDK rozšíření, přejděte na weby dodavatelů, kteří vlastní závislosti, a nainstalujte verze těchto závislostí, které jsou kompatibilní s verzí platformy, kterou je váš projekt Cílení.

1. Restartujte Visual Studio a otevřete aplikaci.

1. Klepněte pravým tlačítkem myši na uzel **Odkazy** nebo **závislosti** v projektu, který chybu způsobil, a zvolte **Přidat odkaz**.

1. Klikněte na kartu **Windows** a potom na dílčí kartu **Rozšíření,** zrušte zaškrtnutí políček u starých sad SDK rozšíření a zaškrtněte políčka u nových sad SDK rozšíření. Klikněte na tlačítko **OK**.

## <a name="add-a-reference-at-design-time"></a>Přidání odkazu v době návrhu

Když vytvoříte odkaz na sestavení v projektu, Visual Studio vyhledá sestavení v následujících umístěních:

- Aktuální adresář projektu. (Tato sestavení můžete najít pomocí karty **Procházet.)**

- Další adresáře projektu ve stejném řešení. (Tato sestavení najdete na kartě **Projekty.)**

> [!NOTE]
> - Všechny projekty obsahují implicitní odkaz na **mscorlib**.
> - Všechny projekty obsahují `System.Core`implicitní `System.Core` odkaz na , i když je odebrán ze seznamu odkazů.
> - Projekty jazyka obsahují implicitní odkaz na aplikaci <xref:Microsoft.VisualBasic>.

## <a name="references-to-shared-components-at-run-time"></a>Odkazy na sdílené součásti za běhu

Za běhu součásti musí být buď ve výstupní cestě projektu nebo v globální mezipaměti sestavení (GAC). Pokud projekt obsahuje odkaz na objekt, který není v jednom z těchto umístění, je nutné zkopírovat odkaz na výstupní cestu projektu při vytváření projektu. Vlastnost <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> označuje, zda má být tato kopie provedena. Pokud je hodnota **True**, odkaz je zkopírován do adresáře projektu při vytváření projektu. Pokud je hodnota **False**, odkaz není zkopírován.

Pokud nasadíte aplikaci, která obsahuje odkaz na vlastní součást, která je registrována v GAC, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> součást nebude nasazena s aplikací, bez ohledu na nastavení. V dřívějších verzích sady Visual <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> Studio můžete nastavit vlastnost na odkaz k zajištění, že sestavení bylo nasazeno. Nyní je nutné ručně přidat sestavení do složky \Bin. Tím se zkontrolují všechny vlastní kódy, což snižuje riziko publikování vlastního kódu, se kterým nejste obeznámeni.

Ve výchozím <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> nastavení je vlastnost nastavena na **hodnotu False,** pokud je sestava nebo součást v globální mezipaměti sestavení nebo je součástí architektury. V opačném případě je hodnota nastavena na **hodnotu True**. Odkazy na projekt na projekt jsou vždy nastaveny na **hodnotu True**.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-net"></a>Odkaz na projekt nebo sestavení, které cílí na jinou verzi rozhraní .NET

Můžete vytvořit aplikace, které odkazují na projekty nebo sestavení, které cílí na jinou verzi rozhraní .NET. Můžete například vytvořit aplikaci, která cílí na rozhraní .NET Framework 4.6, která odkazuje na sestavení, které se zaměřuje na rozhraní .NET Framework 4.5. Pokud vytvoříte projekt, který cílí na starší verzi rozhraní .NET, nelze v tomto projektu nastavit odkaz na projekt nebo sestavení, které cílí na novější verzi.

Další informace naleznete v [tématu Přehled cílení na rozhraní Framework](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Odkazy na projekt

Odkazy na projekt jsou odkazy na projekty, které obsahují sestavení; odkazy na projekt přidáte pomocí karty **Projekty** v dialogovém okně Správce odkazů. Visual Studio můžete najít sestavení při dané cestě k projektu.

Pokud máte projekt, který vytváří sestavení, měli byste odkazovat na projekt a nepoužívat odkaz na soubor (viz níže). Výhodou odkazu projekt na projekt je, že vytvoří závislost mezi projekty v systému sestavení. Závislý projekt bude vytvořen, pokud se změnil od posledního vytvoření referenčního projektu. Odkaz na soubor nevytvoří závislost sestavení, takže je možné vytvořit odkazující projekt bez sestavení závislého projektu a odkaz může být zastaralý. (To znamená, že projekt může odkazovat na dříve sestavenou verzi projektu.) To může mít za následek několik verzí jedné dll je požadováno v adresáři *bin,* což není možné. Dojde-li k tomuto konfliktu, zobrazí se zpráva jako "Upozornění: soubor závislosti v projektu 'projekt' nelze zkopírovat do adresáře spuštění, protože by přepsat odkaz 'soubor.'. Další informace naleznete [v tématech Poradce při potížích s nefunkčními odkazy](../ide/troubleshooting-broken-references.md) a [Postup: Vytvoření a odebrání závislostí projektu](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Odkaz na soubor namísto odkazu projekt na projekt je vytvořen, pokud je cílová verze rozhraní .NET Framework jednoho projektu verze 4.5 a cílová verze druhého projektu je verze 2, 3, 3.5 nebo 4.0.

## <a name="shared-project-references"></a>Odkazy na sdílené projekty

Na rozdíl od většiny ostatních typů projektů *sdílený projekt* nemá žádný binární výstup. Místo toho je kód zkompilován do každého projektu, který na něj odkazuje. [Sdílené projekty](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) umožňují psát společný kód, na který odkazuje řada různých aplikačních projektů. Kód je zkompilován jako součást každého referenčního projektu a může obsahovat direktivy kompilátoru, které pomáhají začlenit funkce specifické pro platformu do základu sdíleného kódu. Přidejte odkaz na sdílený projekt na kartě **Sdílené projekty** v dialogovém okně Správce odkazů.

## <a name="file-references"></a>Odkazy na soubory

Odkazy na soubory jsou přímé odkazy na sestavení mimo kontext projektu sady Visual Studio. Můžete je vytvořit pomocí karty **Procházet** v dialogovém okně Správce odkazů. Odkaz na soubor použijte, pokud máte pouze sestavu nebo součást, a nikoli projekt, který ji vytvoří jako výstup.

## <a name="see-also"></a>Viz také

- [Řešení problémů s poškozenými odkazy](../ide/troubleshooting-broken-references.md)
- [Postup: Přidání nebo odebrání odkazů](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
