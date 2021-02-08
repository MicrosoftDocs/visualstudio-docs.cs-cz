---
title: V sadě Visual Studio SDK | Microsoft Docs
description: Seznamte se s rozšířeními v sadě Visual Studio SDK, včetně architektury sady Visual Studio, komponent, služeb, schémat a nástrojů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2d67c3d9f998c8dd5192363cf8ff8fae2ce4b57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839856"
---
# <a name="inside-the-visual-studio-sdk"></a>Práce se sadou Visual Studio SDK

V této části najdete podrobné informace o rozšířeních sady Visual Studio, včetně architektury sady Visual Studio, součástí, služeb, schémat, nástrojů a podobně jako.

## <a name="extensibility-architecture"></a>Architektura rozšiřitelnosti
 Následující ilustrace znázorňuje architekturu rozšiřitelnosti sady Visual Studio. Sady VSPackage poskytují funkce aplikace, které jsou sdíleny napříč IDE jako služby. Standardní rozhraní IDE také nabízí širokou škálu služeb, například <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , které poskytují přístup k funkcím okna IDE.

 ![Architektura prostředí – grafika](../../extensibility/internals/media/environment.gif "environment") Zobecněné zobrazení architektury sady Visual Studio

## <a name="vspackages"></a>Balíčky VSPackage
 VSPackage jsou softwarové moduly, které tvoří a rozšířily Visual Studio s prvky uživatelského rozhraní, službami, projekty, editory a návrháři. Sady VSPackage jsou střední jednotkou architektury sady Visual Studio. Další informace najdete v tématu [VSPackage](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Prostředí sady Visual Studio poskytuje základní funkce a podporuje křížovou komunikaci mezi komponentami VSPackage a rozšířeními MEF. Další informace naleznete v tématu [prostředí sady Visual Studio](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Pravidla pro práci s uživatelským prostředím
 Pokud plánujete navrhovat nové funkce pro Visual Studio, měli byste se podívat na tyto pokyny v tipech pro návrh a použitelnost: [pokyny pro uživatelské prostředí sady Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Příkazy
 Příkazy jsou funkce, které provádějí úlohy, jako je například tisk dokumentu, aktualizace zobrazení nebo vytvoření nového souboru.

 Když rozšíříte Visual Studio, můžete vytvořit příkazy a zaregistrovat je pomocí prostředí sady Visual Studio. Můžete určit, jak se tyto příkazy zobrazí v integrovaném vývojovém prostředí (IDE), například v nabídce nebo na panelu nástrojů. V nabídce **nástroje** se obvykle zobrazí vlastní příkaz a v nabídce **zobrazení** **se zobrazí** příkaz pro zobrazení okna nástroje.

 Při vytváření příkazu je nutné pro něj také vytvořit obslužnou rutinu události. Obslužná rutina události Určuje, zda je příkaz viditelný nebo povolený, umožňuje upravit jeho text a zaručuje, že příkaz reaguje správně při jeho aktivaci. Ve většině instancí rozhraní IDE zpracovává příkazy pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Příkazy v aplikaci Visual Studio jsou zpracovávány počínaje nejvnitřnějším kontextem příkazu na základě místního výběru a pokračováním do nejvzdálenějšího kontextu v závislosti na globálním výběru. Příkazy přidané do hlavní nabídky jsou okamžitě k dispozici pro skriptování.

 Další informace najdete v tématech [příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Nabídky a panely nástrojů
 Nabídky a panely nástrojů poskytují uživatelům způsob, jak vyvolat příkazy. Nabídky jsou řádky nebo sloupce příkazů, které se obvykle zobrazují jako jednotlivé textové položky v horní části okna nástroje. Podnabídky jsou sekundárními nabídkami, které se zobrazí, když uživatel klikne na příkazy, které obsahují malou šipku. Kontextové nabídky se zobrazí, když uživatel klikne pravým tlačítkem myši na určité prvky uživatelského rozhraní. Mezi běžné názvy nabídek patří **soubor**, **Úpravy**, **zobrazení** a **okno**. Další informace najdete v tématu [rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).

 Panely nástrojů jsou řádky nebo sloupce tlačítek a další ovládací prvky, například pole se seznamem, seznamy a textová pole. Tlačítka panelu nástrojů mají obvykle obrázky ikon, například ikonu složky pro příkaz **otevřít soubor** nebo tiskárnu pro příkaz **Tisk** . Všechny prvky panelu nástrojů jsou přidruženy k příkazům. Po kliknutí na tlačítko na panelu nástrojů se jeho přidružený příkaz spustí. V případě ovládacího prvku rozevíracího seznamu je každá položka v rozevíracím seznamu přidružena k jinému příkazu. Některé ovládací prvky panelu nástrojů, jako je například ovládací prvek rozdělovače, jsou hybrids. Jedna strana ovládacího prvku je tlačítko panelu nástrojů a druhá strana má šipku dolů, která při kliknutí zobrazuje několik příkazů.

## <a name="tool-windows"></a>Okna nástrojů
 Okna nástrojů se používají v integrovaném vývojovém prostředí k zobrazení informací. Příklady oken nástrojů jsou **sady nástrojů**, **Průzkumník řešení**, okno **vlastností** a **webový prohlížeč** .

 Okna nástrojů obvykle nabízejí různé ovládací prvky, se kterými může uživatel pracovat. Například okno **vlastnosti** umožňuje uživateli nastavit vlastnosti objektů, které slouží k určitému účelu. Okno **vlastnosti** je specializované v tomto smyslu, ale také obecné, protože může být použito v mnoha různých situacích. Podobně je okno **výstup** specializované, protože poskytuje textový výstup, ale obecně vzhledem k tomu, že řada subsystémů v aplikaci Visual Studio může použít k poskytnutí výstupu uživateli aplikace Visual Studio.

 Vezměte v úvahu následující obrázek sady Visual Studio, která obsahuje několik oken nástrojů:

 ![Snímek obrazovky](../../extensibility/internals/media/t1gui.png "T1gui")

 Některá okna nástrojů jsou ukotvena společně v jednom podokně, které zobrazuje okno Průzkumník řešení nástrojů a skrývá ostatní okna nástrojů, ale zpřístupňuje je kliknutím na karty. Obrázek ukazuje další okna nástrojů, okno **Seznam chyb** a **výstup** , které je ukotveno společně v jednom podokně.

 Zobrazuje se také hlavní podokno dokumentu, které zobrazuje několik oken editoru. Přestože má systém Windows obvykle pouze jednu instanci (například můžete otevřít pouze jeden **Průzkumník řešení**), okna Editor mohou mít několik instancí, z nichž každý je použit k úpravě samostatného dokumentu, ale všechny jsou ukotveny ve stejném podokně. Obrázek zobrazuje podokno dokumentu, které obsahuje dva okna editoru, jedno okno návrháře formuláře. Všechna okna v podokně dokumentu jsou k dispozici kliknutím na karty, ale okno editoru, které obsahuje soubor EditorPane.cs, je viditelné a aktivní.

 Když rozšíříte aplikaci Visual Studio, můžete vytvořit okna nástrojů, která uživatelům sady Visual Studio umožní pracovat s vaším rozšířením. Můžete také vytvořit vlastní editory, které umožní uživatelům aplikace Visual Studio upravovat dokumenty. Vzhledem k tomu, že se vaše okna nástrojů a editory budou integrovat do sady Visual Studio, nemusíte je naprogramovat, aby je bylo možné správně ukotvit nebo zobrazit na kartě. Pokud jsou správně registrovány v aplikaci Visual Studio, budou automaticky mít typické funkce oken nástrojů a oken dokumentů v aplikaci Visual Studio. Další informace najdete v tématu [rozšíření a přizpůsobení oken nástrojů](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Okna dokumentů
 Okno dokumentu je rámcové podřízené okno okna rozhraní MDI (Multiple Document Interface). Okna dokumentu se obvykle používají k hostování textových editorů, editorů formulářů (označovaných také jako návrháři) nebo ovládacích prvků pro úpravy, ale mohou také hostovat jiné funkční typy. Dialogové okno **nový soubor** obsahuje příklady oken dokumentu, které poskytuje Visual Studio.

 Většina editorů je specifická pro programovací jazyk nebo pro typ souboru, jako jsou stránky HTML, sady rámců, soubory C++ nebo soubory hlaviček. Když v dialogovém okně **nový soubor** vyberete šablonu, uživatel dynamicky vytvoří okno dokumentu pro editor pro typ souboru, který je přidružený k šabloně. Okno dokumentu se také vytvoří, když uživatel otevře existující soubor.

 Okna dokumentu jsou omezená na oblast klienta MDI. Každé okno dokumentu má na začátku kartu a pořadí karet je propojeno s dalšími okny, které mohou být otevřeny v oblasti MDI. Kliknutím pravým tlačítkem myši na kartu okna dokumentu se zobrazí místní nabídka, která obsahuje možnosti pro rozdělení oblasti MDI na více vodorovných nebo svislých skupin karet. Rozdělení oblasti MDI umožňuje zobrazit více souborů současně. Další informace najdete v tématu [okna dokumentů](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Editory
 Editor sady Visual Studio umožňuje přizpůsobit ho a používat pro vlastní typy obsahu prostřednictvím Managed Extensibility Framework (MEF). V mnoha případech nebudete muset vytvořit VSPackage pro rozšíření editoru, i když chcete zahrnout funkce z prostředí (například příkaz nabídky nebo klávesovou zkratku), můžete zkombinovat rozšíření MEF pomocí VSPackage.

 Můžete také vytvořit vlastní editor, například pokud chcete číst a zapisovat do databáze nebo pokud chcete použít návrháře. Můžete také použít externí editor, například Poznámkový blok nebo Microsoft WordPad. Další informace najdete v tématu [rozšíření pro Editor a jazykové služby](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Jazykové služby
 Pokud chcete, aby Editor sady Visual Studio podporoval nová klíčová slova pro programování nebo dokonce nový programovací jazyk, vytvoříte službu jazyka. Každá služba jazyka může implementovat určité funkce editoru úplně, částečně nebo vůbec. V závislosti na tom, jak je nakonfigurováno, může služba jazyka poskytovat zvýrazňování syntaxe, spárování složených závorek, podporu technologie IntelliSense a další funkce v editoru.

 Jádrem jazykové služby je analyzátor a skener. Skener (nebo lexer) rozděluje zdrojový soubor na elementy, které jsou známé jako tokeny, a analyzátor vytváří vztahy mezi těmito tokeny. Při vytváření jazykové služby je nutné implementovat analyzátor a skener, aby aplikace Visual Studio mohla pochopit tokeny a gramatiku jazyka. Můžete vytvořit spravované nebo nespravované jazykové služby. Další informace najdete v tématu [rozšiřitelnost služby starší verze jazyka](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projekty

V aplikaci Visual Studio jsou projekty kontejnery, které vývojáři používají k uspořádání a sestavení zdrojového kódu a dalších prostředků. Projekty umožňují organizovat, sestavovat, ladit a nasazovat zdrojový kód, odkazy na webové služby a databáze a další prostředky. Sady VSPackage mohou rozšíření systému projektu sady Visual Studio, protože poskytují typy projektů, podtypy projektů a vlastní nástroje.

Projekty mohou být také shromažďovány společně v *řešení*, což je seskupení jednoho nebo více projektů, které spolupracují při vytváření aplikace. Informace o projektu a stavu, které se týkají řešení, jsou uloženy ve dvou souborech řešení, v textovém [souboru řešení (. sln)](solution-dot-sln-file.md) a v [souboru možnosti uživatele binárního řešení (. suo)](solution-user-options-dot-suo-file.md). Tyto soubory jsou podobné souborům skupiny (. VBG), které byly použity v dřívějších verzích Visual Basic a v pracovních prostorech (. DSW) a uživatelských možnostech (. opt), které byly použity v dřívějších verzích jazyka C++.

Další informace najdete v tématu [projekty](../../extensibility/internals/projects.md) a [řešení](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Šablony projektů a položek
 Visual Studio obsahuje předdefinované šablony projektů a šablony položek projektu. Můžete také vytvořit vlastní šablony nebo získat šablony z komunity a pak je integrovat do sady Visual Studio. [Galerie kódu MSDN](https://code.msdn.microsoft.com/site/search?query=visual%20studio) je místem, kde můžete přejít k šablonám a rozšířením.

 Šablony obsahují strukturu projektu a základní soubory, které jsou požadovány pro sestavení konkrétního druhu aplikace, ovládacího prvku, knihovny nebo třídy. Pokud chcete vyvíjet software, který se podobá jedné z šablon, vytvořte projekt, který je založen na šabloně, a pak upravte soubory v tomto projektu.

> [!NOTE]
> Tato architektura šablony není pro projekty podporována [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

 Další informace naleznete v tématu [Přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Vlastnosti a možnosti
 V okně **vlastnosti** se zobrazí vlastnosti jedné nebo více vybraných položek: [rozšíření vlastností](../../extensibility/internals/extending-properties.md) stránky obsahuje sady možností, které se vztahují k určité komponentě, jako například programovací jazyk nebo stránky VSPackage: [Možnosti a možnosti](../../extensibility/internals/options-and-options-pages.md). Nastavení jsou všeobecně funkcemi související s uživatelským rozhraním, které je možné importovat a exportovat: [Podpora uživatelských nastavení](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Služby sady Visual Studio
 Služba poskytuje konkrétní sadu rozhraní pro využívání komponent. Sada Visual Studio poskytuje sadu služeb, které mohou být použity všemi komponentami včetně rozšíření. Například služby sady Visual Studio umožňují dynamické zobrazení nebo skrytí oken nástrojů, povolení přístupu k nápovědě, stavovým stavům nebo událostem uživatelského rozhraní. Editor sady Visual Studio také poskytuje služby, které lze importovat pomocí rozšíření editoru. Další informace najdete v tématu [používání a poskytování služeb](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Ladicí program
 Ladicí program je uživatelské rozhraní pro součásti ladění specifické pro jazyk. Pokud jste vytvořili novou jazykovou službu, budete muset vytvořit konkrétní ladicí stroj, který se připojí k ladicímu programu. Další informace najdete v tématu [rozšiřitelnost ladicího programu sady Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Správa zdrojového kódu
 Informace o implementaci modulu plug-in nebo VSPackage správy zdrojového kódu naleznete v tématu [Správa zdrojového kódu](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Průvodci
 Můžete vytvořit průvodce ve spojení s novým typem projektu, aby průvodce mohl pomáhat vašim uživatelům při vytváření nového projektu daného typu. Další informace najdete v tématu [Průvodce](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Vlastní nástroje
 Vlastní nástroje umožňují přidružit nástroj k položce v projektu a spustit tento nástroj pokaždé, když je soubor uložený. Další informace najdete v tématu [vlastní nástroje](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Nástroje VSSDK
 VSSDK obsahuje sadu nástrojů, které možná budete potřebovat, aby bylo možné pracovat s různými aspekty VSPackage. Další informace najdete v tématu [VSSDK Utilities](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Použití Instalační služba systému Windows
 V některých případech může být nutné použít Instalační služba systému Windows místo instalačního programu VSIX: například může být nutné zapisovat do registru. Informace o použití Instalační služba systému Windows s rozšířeními najdete v tématu [Instalace VSPackage pomocí Instalační služba systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Prohlížeč nápovědy
 V aplikaci Help Viewer můžete integrovat vlastní nápovědu a stránky F1. Další informace najdete v tématu [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
