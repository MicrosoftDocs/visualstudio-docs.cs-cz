---
title: Implementace vlastních kategorií a zobrazovat položky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 850e4396c11cbd83f578304eed78a25042185a25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894635"
---
# <a name="implement-custom-categories-and-display-items"></a>Implementovat vlastní kategorie a zobrazení položek
VSPackage může poskytnout kontrolu nad písma a barvy jeho textu, aby [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE) prostřednictvím vlastní kategorie a zobrazit položky.

 Vlastní kategorie a zobrazení položek **písma a barvy** stránku vlastností. Chcete-li otevřít **písma a barvy** vlastnost na stránce **nástroje** nabídky, klikněte na tlačítko **možnosti**. Rozbalte **prostředí** a potom klikněte na tlačítko **písma a barvy**.

 Při používání tohoto mechanismu, musí implementovat rozšíření VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> rozhraní a jeho přidružené rozhraní.

 V zásadě, tento mechanismus lze použít k úpravě všech stávajících **zobrazení položek** a **kategorie** , které je obsahují. Ale neměli použít ke změně **Text EditorCategory** nebo jeho **zobrazení položek**. Další informace najdete v tématu [přehled písma a barvy](../extensibility/font-and-color-overview.md).

 Chcete-li implementovat vlastní **kategorie** nebo **zobrazení položek**, VSPackage musí:

- Vytvořte nebo Identifikujte kategorií v registru.

   Implementace rozhraní IDE **písma a barvy** stránku vlastností používá tyto informace se správně dotázat služba podporující dané kategorie.

- Vytvořte nebo Identifikujte skupin (volitelné) v registru.

   Může být užitečné k definování skupiny, která představuje sjednocení dvou nebo více kategorií. Pokud skupina je definována, rozhraní IDE automaticky sloučí podkategorie a distribuuje zobrazení položek v rámci skupiny.

- Implementace podpora integrované vývojové prostředí.

- Zpracování změn písma a barvy.

  Informace najdete v tématu [přístup uložená nastavení písem a barev](../extensibility/accessing-stored-font-and-color-settings.md).

## <a name="to-create-or-identify-categories"></a>K vytvoření nebo určení kategorie

- Vytvořit zvláštní druh položky registru kategorie *[HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<verze sady Visual Studio >*\FontAndColors\\ `<Category>`]*

   *\<Kategorie >* je nelokalizovaný název kategorie.

- Naplnění registru pomocí dvou hodnot:

  |Název|Typ|Data|Popis|
  |----------|----------|----------|-----------------|
  |Kategorie|REG_SZ|GUID|Identifikátor GUID vytvořit pro identifikaci kategorii.|
  |Balíček|REG_SZ|GUID|Identifikátor GUID služby VSPackage, která podporuje kategorii.|

  Služba uvedený v registru musí poskytovat implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> pro odpovídající kategorii.

## <a name="to-create-or-identify-groups"></a>Vytvořte nebo Identifikujte skupiny

- Vytvořit zvláštní druh položky registru kategorie *[HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<verze sady Visual Studio >*\FontAndColors\\*  \<skupiny >*]*

   *\<skupiny >* je nelokalizovaný název skupiny.

- Naplnění registru pomocí dvou hodnot:

  |Název|Typ|Data|Popis|
  |----------|----------|----------|-----------------|
  |Kategorie|REG_SZ|GUID|Identifikujte skupinu vytvoří identifikátor GUID.|
  |Balíček|REG_SZ|GUID|Identifikátor GUID služby, která podporuje kategorii.|

  Služba uvedený v registru musí poskytovat implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> pro příslušné skupiny.

## <a name="to-implement-ide-support"></a>K implementaci podpora integrované vývojové prostředí

- Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, který vrátí buď <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> rozhraní nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> rozhraní IDE pro každou **kategorie** nebo skupině zadaným identifikátorem GUID.

- Pro každý **kategorie** podporuje, VSPackage implementuje samostatnou instanci <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> rozhraní.

- Metody implementovány pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> nezajistil integrované vývojové prostředí s:

  -   Seznamy **zobrazení položek** v **kategorie.**

  -   Lokalizovatelné názvy **zobrazení položek**.

  -   Zobrazení informací pro každého člena **kategorie**.

  > [!NOTE]
  >  Každý **kategorie** musí obsahovat alespoň jeden **položky zobrazení**.

- Využívá integrovaného vývojového prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> rozhraní definovat sjednocení několik kategorií.

   Jeho implementace poskytuje integrované vývojové prostředí s:

  -   Seznam **kategorie** , která tvoří danou skupinu.

  -   Přístup k instancím typu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> podporuje každý **kategorie** v rámci skupiny.

  -   Názvy zdrojů lokalizovatelných skupin.

- Aktualizuje se rozhraní IDE:

   Rozhraní IDE ukládá do mezipaměti informace o **písma a barvy** nastavení. Proto po jakékoliv úpravě rozhraní IDE **písma a barvy** konfigurace, doporučuje se ujistěte se, že mezipaměť je aktuální.

  Aktualizace mezipaměti se provádí prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> rozhraní a může být provedena globálně, nebo jenom na vybraných položek.

## <a name="to-handle-font-and-color-changes"></a>Pro případ změn písma a barvy
 Pro podporu správně zabarvení textu, který zobrazí VSPackage, zabarvení služba podporující sady VSPackage musí odpovědět na uživatelem iniciované změny provedené **písma a barvy** stránku vlastností. VSPackage provádí toto:

-   Zpracování událostí generovaných IDE implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> rozhraní.

     Integrované vývojové prostředí volá metodu odpovídající následující úpravy uživatele **písma a barvy** stránky. Například volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> metody, pokud je vybrána nového písma.

     -nebo-

-   Dotazování rozhraní IDE pro změny.

     To lze provést prostřednictvím systému implementované <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní. I když především pro podporu trvalost, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> metodu je možné získat informace o písma a barvy pro **zobrazení položek**. Další informace najdete v tématu [přístup uložená nastavení písem a barev](../extensibility/accessing-stored-font-and-color-settings.md).

    > [!NOTE]
    >  Chcete-li zajistit, aby získala při dotazování na výsledky jsou správné, může být vhodné použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> rozhraní k určení, pokud se před voláním metody načítání potřebuje vyprázdnění mezipaměti a aktualizace <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- [Získání informací o písma a barvy pro barevné zvýraznění textu](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Přístup uložená nastavení písma a barvy](../extensibility/accessing-stored-font-and-color-settings.md)
- [Postupy: přístup k vestavěné písma a barvy schéma](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)
- [Přehled písma a barvy](../extensibility/font-and-color-overview.md)