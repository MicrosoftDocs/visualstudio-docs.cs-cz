---
title: 'Postupy: přístup k vestavěné písma a barvy schéma | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 295f6d26d086914bf75d5744ca47594dfefb6591
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911249"
---
# <a name="how-to-access-the-built-in-fonts-and-color-ccheme"></a>Postupy: přístup k vestavěné písma a barev ccheme
Integrovaného vývojového prostředí (IDE) sady Visual Studio obsahuje schéma písma a barvy, který je spojen s okno editoru. Toto schéma prostřednictvím můžete přistupovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní.

 Pokud chcete použít integrované písma a barvy schéma, musíte VSPackage:

- Definujte kategorie pro použití s výchozí služba písma a barvy.

- Zaregistrujte si kategorie ve výchozí server písma a barvy.

- Doporučte rozhraní IDE, že konkrétní okno používá integrované zobrazit položky a kategorie pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> rozhraní.

  Integrované vývojové prostředí používá výsledný kategorie jako popisovač okna. Název kategorie se zobrazí v **zobrazit nastavení pro:** v rozevíracím seznamu **písma a barvy** stránku vlastností.

## <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Chcete-li definovat kategorie pomocí integrované písmo a barvy

1.  Vytvořte libovolný identifikátor GUID.

     Tento identifikátor GUID slouží k jednoznačné identifikaci kategorii. Rozhraní IDE výchozí písma a barvy specifikace opětovně používá tuto kategorii.

    > [!NOTE]
    >  Při načítání dat písma a barvy s <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> nebo jiných rozhraní rozšíření VSPackages použít tento identifikátor GUID k odkazování předdefinované informace.

2.  Název kategorie musí přidat do tabulky řetězců uvnitř sady VSPackage prostředky (*.rc*) souboru, takže může být lokalizována, podle potřeby při zobrazení v rozhraní IDE.

     Další informace najdete v tématu [přidání nebo odstranění řetězce](/cpp/windows/adding-or-deleting-a-string).

### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>K registraci kategorie pomocí integrované písmo a barvy

1.  Vytvořte zvláštní druh položky registru kategorie v následujícím umístění:

     *[HKLM\SOFTWARE\Microsoft \Visual Studio\\\<verze sady Visual Studio > \FontAndColors\\\<kategorie >*]

     *\<Kategorie >* je nelokalizovaný název kategorie.

2.  Naplnění registru uložených písma a barvy schéma pomocí čtyři hodnoty:

    |Název|Typ|Data|Popis|
    |----------|----------|----------|-----------------|
    |Kategorie|REG_SZ|GUID|Libovolné GUID, který určuje kategorii, která obsahuje základní schéma písma a barvy.|
    |Balíček|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Všechny balíčky VSPackages, které používají výchozí písmo a barvu konfigurace používá tento identifikátor GUID.|
    |NameID|REG_DWORD|ID|ID prostředku název lokalizovatelné kategorie v sady VSPackage.|
    |ToolWindowPackage|REG_SZ|GUID|Identifikátor GUID balíčku VSPackage implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní.|

### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>K zahájení používání nástroje poskytované systémem písma a barvy

1. Vytvoření instance <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> rozhraní jako součást implementace okna a inicializace.

2. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodu k získání instance <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> rozhraní odpovídá aktuální <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> instance.

3. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> dvakrát.

   - Volání s jednou `VSEDITPROPID_ViewGeneral_ColorCategory`jako argument.

   - Volání s jednou `VSEDITPROPID_ViewGeneral_FontCategory` jako argument.

     Toto nastaví a poskytuje výchozí písmo a barvy služby jako vlastnost okna.

## <a name="example"></a>Příklad
 Následující příklad inicializuje použití předdefinovaných písma a barvy.

```cpp
CComVariant vt;
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);
if (spPropCatContainer != NULL){
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,
                                                          &spPropContainer))){
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);
    }
}
```

## <a name="see-also"></a>Viz také:

- [Použití písem a barev](../extensibility/using-fonts-and-colors.md)
- [Získání informací o písma a barvy pro barevné zvýraznění textu](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Přístup uložená nastavení písma a barvy](../extensibility/accessing-stored-font-and-color-settings.md)
- [Přehled písma a barvy](../extensibility/font-and-color-overview.md)