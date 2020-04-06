---
title: Vytváření vlastních editorů a návrhářů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9f56b82225e1e40782b6753bea03d3c1780f596
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739484"
---
# <a name="create-custom-editors-and-designers"></a>Vytvoření vlastních editorů a návrhářů

Integrované vývojové prostředí sady Visual Studio (IDE) může hostovat různé typy editoru:

- Základní editor visual ateliéru

- Vlastní editory

- Externí redakce

- Návrháři

Následující informace vám pomohou vybrat typ editoru, který potřebujete.

## <a name="types-of-editor"></a>Typy editoru

Informace o základní editor u sady Visual Studio naleznete [v tématu Rozšíření editoru a jazykových služeb](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Vlastní editory
 Vlastní editor je ten, který je určen pro práci ve specializovaných okolností. Můžete například vytvořit editor, jehož funkcí je čtení a zápis dat do určitého úložiště, jako je například server Microsoft Exchange. Zvolte vlastní editor, pokud chcete editor, který pracuje pouze s typem projektu, nebo pokud chcete editor, který má pouze několik konkrétních příkazů. Všimněte si však, že uživatelé nebudou moci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] používat vlastní editor k úpravám standardních projektů.

 Vlastní editor můžete použít editor factory a přidat informace o editoru do registru. Typ projektu přidružené k vlastní editor však můžete vytvořit instanci vlastní editor jinými způsoby.

 Vlastní editor můžete použít buď na místě aktivace nebo zjednodušené vkládání k implementaci zobrazení.

### <a name="external-editors"></a>Externí redaktoři
 Externí editory jsou editory, které nejsou integrovány do sady Visual Studio, například Microsoft Word, Poznámkový blok nebo Aplikace Microsoft FrontPage. Takový editor můžete volat, pokud mu například předáváte text z vašeho balíčku VSPackage. Externí editory zaregistrovat sami a lze použít mimo Visual Studio. Když zavoláte externí editor a může být vložen do okna hostitele, zobrazí se v okně v integrovaném rozhraní IDE. Pokud ne, pak ide vytvoří samostatné okno pro něj.

 Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> nastaví prioritu dokumentu <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> pomocí výčtu. Pokud `DP_External` je zadána hodnota, soubor lze otevřít externím editorem.

## <a name="editor-design-decisions"></a>Rozhodnutí editora návrhu
 Následující otázky týkající se návrhu vám pomohou vybrat typ editoru, který nejlépe vyhovuje vaší aplikaci:

- Uloží vaše aplikace svá data do souborů nebo ne? Pokud bude ukládat svá data do souborů, budou ve vlastním nebo standardním formátu?

   Pokud používáte standardní formát souboru, ostatní typy projektů kromě projektu budou moci otevřít a číst a zapisovat data do nich. Pokud však používáte vlastní formát souboru, bude možné otevřít a číst a zapisovat data pouze váš typ projektu.

   Pokud váš projekt používá soubory, měli byste přizpůsobit standardní editor. Pokud váš projekt nepoužívá soubory, ale spíše používá položky v databázi nebo jiném úložišti, měli byste vytvořit vlastní editor.

- Potřebuje váš editor hostovat ovládací prvky ActiveX?

   Pokud editor hostuje ovládací prvky ActiveX, implementujte editor aktivace na místě, jak je uvedeno [v aktivaci na místě](/visualstudio/misc/in-place-activation?view=vs-2015). Pokud nehostuje ovládací prvky ActiveX, použijte buď zjednodušený editor vkládání, nebo přizpůsobte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] výchozí editor.

- Bude váš editor podporovat více zobrazení? Pokud chcete, aby zobrazení editoru byla viditelná současně s výchozím editorem, je nutné podporovat více zobrazení.

   Pokud editor potřebuje podporovat více zobrazení, musí být data dokumentu a objekty zobrazení dokumentu pro editor samostatnými objekty. Další informace naleznete v [tématu Podpora více zobrazení dokumentu](../extensibility/supporting-multiple-document-views.md).

   Pokud editor podporuje více zobrazení, plánujete [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] použít implementaci<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> (objekt) textové vyrovnávací paměti základního editoru pro datový objekt dokumentu? To znamená, že chcete podpořit zobrazení editoru vedle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sebe s editorem jádra? Schopnost to provést je základem návrháře formulářů..

- Pokud potřebujete hostovat externí editor , může být [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]editor vložen uvnitř ?

   Pokud může být vložen, měli byste vytvořit okno hostitele pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> externí editor <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> a potom volat `DP_External`metodu a nastavit hodnotu výčtu na . Pokud editor nelze vložit, rozhraní IDE automaticky vytvoří samostatné okno pro něj.

## <a name="in-this-section"></a>V tomto oddílu

[Návod: Vytvoření vlastního editoru](../extensibility/walkthrough-creating-a-custom-editor.md)\
Vysvětluje, jak vytvořit vlastní editor.

[Návod: Přidání funkcí do vlastního editoru](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Vysvětluje, jak přidat funkce do vlastního editoru.

[Inicializace návrháře a konfigurace metadat](../extensibility/designer-initialization-and-metadata-configuration.md)\
Vysvětluje, jak inicializovat návrháře.

[Dodávat podporu pro odvádělte návrhářům](../extensibility/supplying-undo-support-to-designers.md)\
Vysvětluje, jak poskytnout podporu pro návrháře.

[Syntaxe barvení ve vlastních editorech](../extensibility/syntax-coloring-in-custom-editors.md)\
Vysvětluje rozdíl mezi vybarvením syntaxe v editoru jádra a ve vlastních editorech.

[Zobrazení dat dokumentů a dokumentů ve vlastních editorech](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Vysvětluje, jak implementovat data dokumentu a zobrazení dokumentů ve vlastních editorech.

## <a name="related-sections"></a>Související oddíly

[Starší rozhraní v editoru](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
Vysvětluje, jak získat přístup k editoru jádra pomocí staršího rozhraní API.

[Vývoj služby starších jazyků](../extensibility/internals/developing-a-legacy-language-service.md)\
Vysvětluje, jak implementovat jazykovou službu.

[Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Vysvětluje, jak vytvořit prvky uživatelského [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]rozhraní, které odpovídají zbytku .

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
