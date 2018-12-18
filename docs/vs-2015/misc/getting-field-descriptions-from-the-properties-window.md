---
title: Získávání popisy pole v okně Vlastnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: fc5d2c8553ccdb6c554f9a8364e9fd21eaa324d1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814789"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Získávání popisy pole z okna Vlastnosti
V dolní části **vlastnosti** okně oblasti popisu zobrazí informace související s vybranou vlastnost pole. Tato funkce je ve výchozím nastavení zapnutá. Pokud chcete skrýt pole Popis, klikněte pravým tlačítkem myši **vlastnosti** okno a klikněte na tlačítko **popis**. Tím také odstraněn znak zaškrtnutí vedle položky **popis** title v nabídce okno. Pole lze zobrazit znovu pomocí stejných kroků, chcete-li přepnout **popis** zpět na.  
  
 Informace v poli popisu pocházejí z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Každá metoda, rozhraní, coclass a tak dále může mít nelokalizované `helpstring` atribut v knihovně typů. **Vlastnosti** okno načte řetězec z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Chcete-li zadat řetězce lokalizované nápovědy  
  
1. Přidat `helpstringdll` atribut příkaz library v knihovně typů (`typelib`).  
  
   > [!NOTE]
   >  Tento krok je volitelný, pokud knihovna typů nachází v objektový soubor knihovny (.olb).  
  
2. Zadejte `helpstringcontext` atributy pro řetězce. Můžete také určit `helpstring` atributy.  
  
    Tyto atributy se liší od `helpfile` a `helpcontext` atributy, které jsou obsaženy ve skutečné chm témata nápovědy souboru.  
  
   Načíst informace o popisu, který se má zobrazit jako název zvýrazněný vlastnost **vlastnosti** volání okno <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> pro vlastnost, která je vybrána, zadáte požadované `lcid` atribut pro výstupní řetězec. Interně <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> Vyhledá zadaný v souboru .dll `helpstringdll` atribut a volání `DLLGetDocumentation` na tento soubor .dll pomocí zadaného kontextu a `lcid` atribut.  
  
   Signatura a implementace `DLLGetDocumentation` jsou:  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation` Funkce musí být definovaný v souboru .def knihovny DLL export.  
  
 Interně je vytvořen soubor olb, což je ve skutečnosti knihovny DLL. Tato knihovna DLL obsahuje jeden prostředek, souboru typu knihovna (.tlb) a jeden exportované funkce `DLLGetDocumentation`.  
  
 V případě .olb soubory `helpstringdll` atribut je volitelný, protože je stejný soubor, který obsahuje samotný soubor .tlb.  
  
 Chcete-li získat řetězců se zobrazí v **popisy** podokno, tedy minimální, je nutné provést je zadejte `helpstring` atribut v knihovně typů. Pokud chcete tyto řetězce lokalizaci, budete muset zadat `helpstringdll` (volitelné) atribut a `helpstringcontext` atribut (povinné) a implementujte `DLLGetDocumentation`.  
  
 Nejsou žádná další rozhraní, které je třeba k implementaci při získávání lokalizovaných informací prostřednictvím vaší idl `helpstringcontext` atribut a `DLLGetDocumentation`.  
  
 Jiný způsob, jak získat lokalizovaný název a popis vlastnosti je implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Další informace týkající se implementace této metody naleznete v tématu [vlastností pole a rozhraní okna](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Vlastnosti pole a rozhraní okna](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Rozšíření vlastností](../extensibility/internals/extending-properties.md)   
 [helpstringdll –](http://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [helpstring](http://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext –](http://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [HelpContext](http://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [Soubor nápovědy](http://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](http://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)