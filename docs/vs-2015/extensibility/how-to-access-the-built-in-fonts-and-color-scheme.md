---
title: 'Postupy: přístup k vestavěným písmům a barevnému schématu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685312"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Postupy: Přístup k předdefinovaným písmům a barevnému schématu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Integrované vývojové prostředí (IDE) sady Visual Studio má schéma písem a barev, které je spojeno s oknem editoru. K tomuto schématu máte přístup prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní.  
  
 Chcete-li použít Vestavěná Schémata písem a barev, VSPackage musí:  
  
- Definujte kategorii, která se má použít u výchozích písem a barev služby.  
  
- Zaregistrujte kategorii pomocí výchozích písem a barev serveru.  
  
- Poradí rozhraní IDE, které konkrétní okno používá předdefinované položky a kategorie zobrazení, pomocí `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` rozhraní a.  
  
  Rozhraní IDE používá výslednou kategorii jako popisovač okna. Název kategorie se zobrazí v rozevíracím seznamu **Zobrazit nastavení pro:** na stránce vlastností **písma a barvy** .  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Definování kategorie pomocí vestavěných písem a barev  
  
1. Vytvořte libovolný identifikátor GUID.  
  
    Tento identifikátor GUID slouží k jednoznačné identifikaci kategorie<strong>.</strong> Tato kategorie znovu používá výchozí písma a barvy v integrovaném vývojovém prostředí (IDE).  
  
   > [!NOTE]
   > Při načítání písma a barev dat pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> nebo jiných rozhraní VSPackage používají tento identifikátor GUID k odkazování na předdefinované informace.  
  
2. Název kategorie musí být přidán do tabulky řetězce v souboru prostředků sady VSPackage (. RC), aby mohl být v rámci zobrazení v integrovaném vývojovém prostředí (IDE) lokalizován podle potřeby.  
  
    Další informace najdete v tématu [Přidání nebo odstranění řetězce](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Registrace kategorie pomocí vestavěných písem a barev  
  
1. Vytvořte speciální typ položky registru kategorie v následujícím umístění:  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<Category>* ]  
  
     *\<Category>* je nelokalizovaný název kategorie.  
  
2. Naplnění registru pro použití burzovních písem a barevného schématu se čtyřmi hodnotami:  
  
    |Název|Typ|Data|Popis|  
    |----------|----------|----------|-----------------|  
    |Kategorie|REG_SZ|Identifikátor GUID|Libovolný identifikátor GUID, který identifikuje kategorii obsahující zásobu písma a barevného schématu.|  
    |Balíček|REG_SZ|Identifikátor GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Tento identifikátor GUID je používán všemi VSPackage, které používají výchozí nastavení písma a barev.|  
    |NameID|REG_DWORD|ID|ID prostředku lokalizovatelnýho názvu kategorie v VSPackage|  
    |ToolWindowPackage|REG_SZ|Identifikátor GUID|Identifikátor GUID VSPackage, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Zahájení používání písem a barev poskytovaných systémem  
  
1. Vytvořte instanci `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` rozhraní v rámci implementace a inicializace okna.  
  
2. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodu pro získání instance `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` rozhraní odpovídající aktuální <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> instanci.  
  
3. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> dvakrát.  
  
   - Zavolejte jednou `VSEDITPROPID_ViewGeneral_ColorCategory` jako argument.  
  
   - Zavolejte jednou `VSEDITPROPID_ViewGeneral_FontCategory` jako argument.  
  
     Tato sada nastavuje a zpřístupňuje výchozí písma a barvy služeb jako vlastnost okna.  
  
## <a name="example"></a>Příklad  
 Následující příklad inicializuje použití vestavěných písem a barev.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Používání písem a barev](../extensibility/using-fonts-and-colors.md)   
 [Získání informací o písmech a barvách pro obarvení textu](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Přístup k uloženým písmům a nastavením barev](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Přehled písem a barev](../extensibility/font-and-color-overview.md)
