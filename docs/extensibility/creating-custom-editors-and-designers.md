---
title: Vytváření vlastních editorů a návrhářů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 05eeae4901af8780927e0ce0577b385ee9ffa371
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950898"
---
# <a name="create-custom-editors-and-designers"></a>Vytváření vlastních editorů a návrhářů
Integrovaného vývojového prostředí (IDE) sady Visual Studio může hostovat různé druhy editoru:  
  
- Základní editor sady Visual Studio  
  
- Vlastních editorech  
  
- Externí editory  
  
- Návrháři  
  
  Následující informace vám umožňuje vybrat typ editoru, které potřebujete.  
  
## <a name="types-of-editor"></a>Typy editoru  
 Informace o základní editor sady Visual Studio najdete v tématu [rozšířit jazyk a editor služby](../extensibility/extending-the-editor-and-language-services.md).  
  
### <a name="custom-editors"></a>Vlastních editorech  
 Vlastní editor je ten, který je navržen pro práci v specializované okolností. Můžete vytvořit editor jehož funkce je pro čtení a zápis dat do konkrétního úložiště, jako je Microsoft Exchange server. Pokud chcete editor, který spolupracuje s vaší typ projektu, nebo pokud chcete, aby editor, který má několik konkrétní příkazy, zvolte vlastní editor. Upozorňujeme, že uživatelé nebudou moct použít vlastní editor k úpravě standard [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekty.  
  
 Vlastní editor můžete použít objekt pro vytváření editoru a přidejte informace o editoru do registru. Typ projektu, který je přidružený k vlastní editor lze vytvořit instanci editoru vlastních jinými způsoby.  
  
 Vlastní editor, můžete použít k implementaci zobrazení aktivace na místě nebo zjednodušená vkládání.  
  
### <a name="external-editors"></a>Externí editory  
 Externí editory jsou editory, které nejsou integrované do sady Visual Studio, jako je například Microsoft Word, Poznámkový blok nebo Microsoft FrontPage. Takové editor může volat, pokud například předávání text k němu z vašeho balíčku VSPackage. Externích editorech mimo sadu Visual Studio lze použít se registrují. Při volání externí editor a může být integrován do hostitelského okna, pak jej zobrazí v okně v integrovaném vývojovém prostředí. Pokud ne, pak IDE vytvoří pro ni samostatném okně.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Metoda nastaví prioritu dokumentu s použitím <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> výčtu. Pokud `DP_External` není zadána hodnota, ho může otevřít externí editor.  
  
## <a name="editor-design-decisions"></a>Rozhodnutí o návrhu editoru  
 Následující dotazy týkající se návrhu vám pomůže zvolit typ editoru nejlepší vhodné pro vaši aplikaci:  
  
- Vaše aplikace uloží svoje data v souborech nebo ne? Pokud svá data se uloží v souborech, že bude ve formátu vlastních nebo standardních?  
  
   Pokud používáte standardní formát souboru, budou ostatní typy projektů, kromě projektu pro otevírání a čtení a zápisu dat do nich. Pokud používáte vlastní formát, ale pouze typ projektu bude pro otevírání a čtení a zápisu dat do nich.  
  
   Pokud váš projekt používá soubory, pak můžete přizpůsobit standardní editor. Pokud váš projekt nepoužívá soubory, ale místo toho používá položky v databázi nebo jiného úložiště, měli byste vytvořit vlastní editor.  
  
- Potřebuje váš editor k hostování ovládacích prvků ActiveX?  
  
   Pokud editor hostuje ovládací prvky ActiveX, editoru aktivace na místě, jak je uvedeno v pak implementovat [aktivace na místě](../extensibility/in-place-activation.md). Pokud není hostitelem ovládacích prvků ActiveX, pak použijte zjednodušená vkládání editor nebo přizpůsobení [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] výchozí editor.  
  
- Editor bude podporovat více zobrazení? Pokud chcete, aby zobrazení editoru mají být zobrazeny ve stejnou dobu jako výchozí editor, musí podporovat několik zobrazení.  
  
   Pokud editor musí podporovat více zobrazení, data dokumentu a objekty zobrazení dokumentu v editoru musí být samostatné objekty. Další informace najdete v tématu [podporovat více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md).  
  
   Pokud editor podporuje několik zobrazení, máte v úmyslu použít [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] základní implementaci vyrovnávací paměti textu editoru (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objekt) pro váš datový objekt dokumentu? To znamená, že chcete podporovat váš editor zobrazení – souběžně s [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] základní editor? Tuto možnost je základem Návrhář formulářů...  
  
- Pokud potřebujete k hostování externím editoru, editoru jde vložit uvnitř [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
   Pokud může být vložen, by měl vytvořit okno hostitele pro externí editor a poté zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metoda a nastavte <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> hodnotu výčtu pro `DP_External`. Pokud editoru nemůže být vložený, rozhraní IDE vytvoří pro ni automaticky samostatném okně  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Návod: Vytvoření vlastního editoru](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Vysvětluje, jak vytvořit vlastní editor.  
  
 [Návod: Přidání funkcí do vlastního editoru](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Vysvětluje, jak přidat funkce do vlastní editor.  
  
 [Návrháře konfigurace inicializace a metadat](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Vysvětluje, jak inicializovat návrháře.  
  
 [Podpora pro vracení zpět dodávek do návrháře](../extensibility/supplying-undo-support-to-designers.md)  
 Vysvětluje, jak poskytovat podpora pro vracení zpět pro profesionální návrháře.  
  
 [Barevné zvýrazňování syntaxe ve vlastních editorech](../extensibility/syntax-coloring-in-custom-editors.md)  
 Vysvětluje rozdíl mezi barevné zvýrazňování v základní editor a ve vlastních editorech syntaxe.  
  
 [Data dokumentu a zobrazení dokumentu ve vlastních editorech](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Vysvětluje, jak implementovat dat dokumentů a zobrazení dokumentu ve vlastních editorech.  
  
## <a name="related-sections"></a>Související oddíly  
 [Starší verze rozhraní v editoru](../extensibility/legacy-interfaces-in-the-editor.md)  
 Vysvětluje, jak získat přístup k základní editor pomocí starší verze rozhraní API.  
  
 [Vývoj služby starší verze jazyka](../extensibility/internals/developing-a-legacy-language-service.md)  
 Vysvětluje, jak implementovat službu jazyka.  
  
 [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Vysvětluje, jak vytvořit prvky uživatelského rozhraní, které odpovídají zbytek [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Viz také:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>