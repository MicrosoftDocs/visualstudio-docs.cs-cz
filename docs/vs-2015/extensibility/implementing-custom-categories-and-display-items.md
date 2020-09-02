---
title: Implementace vlastních kategorií a zobrazení položek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 474d5c66507b56bea609568b6acfe9f5eff75e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796834"
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementace vlastních kategorií a položek zobrazení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage může poskytovat řízení písem a barev jeho textu do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí (IDE) prostřednictvím vlastních kategorií a zobrazení položek.  
  
 Vlastní kategorie a zobrazované položky jsou na stránce vlastností **písma a barvy** . Chcete-li otevřít stránku vlastností **písma a barvy** , v nabídce **nástroje** klikněte na příkaz **Možnosti**. Rozbalte položku **prostředí** a potom klikněte na možnost **písma a barvy**.  
  
 Při použití tohoto mechanismu musí sady VSPackage implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> rozhraní a jeho přidružená rozhraní.  
  
 V zásadě lze tento mechanismus použít pro úpravu všech existujících **položek zobrazení** a **kategorií** , které je obsahují. Neměli byste je ale používat k úpravě **EditorCategory textu** ani jeho **položek zobrazení**. Další informace najdete v tématu [Přehled písma a barev](../extensibility/font-and-color-overview.md).  
  
 Chcete-li implementovat vlastní **kategorie** nebo **Zobrazit položky**, VSPackage musí:  
  
- Vytvořte nebo Identifikujte kategorie v registru.  
  
   Implementace rozhraní IDE stránky vlastností **písma a barvy** používá tyto informace k řádnému dotazování na službu, která podporuje danou kategorii.  
  
- V registru vytvořte nebo Identifikujte skupiny (volitelné).  
  
   Může být užitečné definovat skupinu, která představuje sjednocení dvou nebo více kategorií. Pokud je definovaná skupina, IDE automaticky sloučí podkategorie a rozloží zobrazované položky v rámci skupiny.  
  
- Implementujte podporu IDE.  
  
- Zpracuje změny písma a barev.  
  
  Informace najdete v tématu [přístup k uloženým písmům a nastavením barev](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Chcete-li vytvořit nebo identifikovat kategorie  
  
- Vytvoření speciálního typu položky registru kategorie v rámci [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ `<Category>` ]  
  
   *\<Category>* je nelokalizovaný název kategorie.  
  
- Naplňte registr dvěma hodnotami:  
  
  |Název|Typ|Data|Popis|  
  |----------|----------|----------|-----------------|  
  |Kategorie|REG_SZ|Identifikátor GUID|Identifikátor GUID vytvořený k identifikaci kategorie|  
  |Balíček|REG_SZ|Identifikátor GUID|Identifikátor GUID služby VSPackage, který podporuje kategorii|  
  
  Služba zadaná v registru musí poskytovat implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> pro odpovídající kategorii.  
  
## <a name="to-create-or-identify-groups"></a>Vytvoření nebo identifikace skupin  
  
- Vytvoření speciálního typu položky registru kategorie v rámci [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<group>* ]  
  
   *\<group>* je nelokalizovaný název skupiny.  
  
- Naplňte registr dvěma hodnotami:  
  
  |Název|Typ|Data|Popis|  
  |----------|----------|----------|-----------------|  
  |Kategorie|REG_SZ|Identifikátor GUID|Identifikátor GUID vytvořený k identifikaci skupiny|  
  |Balíček|REG_SZ|Identifikátor GUID|Identifikátor GUID služby, která podporuje kategorii|  
  
  Služba zadaná v registru musí poskytovat implementaci `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` pro odpovídající skupinu.  
  
## <a name="to-implement-ide-support"></a>Implementace podpory IDE  
  
- Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A> , což vrátí <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> rozhraní `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` IDE pro každou **kategorii** nebo identifikátor GUID skupiny, a to buď rozhraní, nebo rozhraní.  
  
- Pro každou **kategorii** , kterou podporuje, VSPackage implementuje samostatnou instanci <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> rozhraní.  
  
- Metody implementované pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> musí poskytovat integrované vývojové prostředí (IDE) s:  
  
  - Seznam **položek zobrazení** v **kategorii**  
  
  - Lokalizovatelné názvy pro **zobrazované položky**  
  
  - Zobrazí informace pro každého člena **kategorie**.  
  
  > [!NOTE]
  > Každá **kategorie** musí obsahovat alespoň jednu **zobrazovanou položku**.  
  
- Rozhraní IDE používá `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` rozhraní k definování sjednocení několika kategorií.  
  
   Jeho implementace poskytuje integrované vývojové prostředí (IDE) s:  
  
  - Seznam **kategorií** , které tvoří danou skupinu.  
  
  - Přístup k instancím <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> podporujícím jednotlivé **kategorie** v rámci skupiny.  
  
  - Lokalizovatelné názvy skupin.  
  
- Aktualizuje se rozhraní IDE:  
  
   Rozhraní IDE ukládá informace o nastavení **písma a barev** do mezipaměti. Proto je po každé změně konfigurace **písma a barev** IDE vhodné zajistit, aby byla mezipaměť aktuální.  
  
  Aktualizace mezipaměti se provádí prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> rozhraní a je možné ji provést globálně nebo jenom na vybraných položkách.  
  
## <a name="to-handle-font-and-color-changes"></a>Zpracování změn písma a barev  
 Aby bylo možné správně podporovat barevné nabarvení textu, který VSPackage zobrazuje, musí služba coloring, která podporuje VSPackage, reagovat na změny iniciované uživatelem, které provedly prostřednictvím stránky vlastností **písma a barvy** . VSPackage to dělá takto:  
  
- Zpracování událostí generovaných rozhraním IDE implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> rozhraní.  
  
     Rozhraní IDE volá příslušnou metodu podle uživatelských úprav stránky **písma a barvy** . Například volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> metodu, pokud je vybráno nové písmo.  
  
     -nebo-  
  
- Cyklické dotazování na rozhraní IDE pro změny.  
  
     To lze provést prostřednictvím rozhraní implementovaného systémem <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . I když především pro podporu trvalosti, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> lze metodu použít k získání informací o písmech a barvách pro **zobrazení položek**. Další informace najdete v tématu [přístup k uloženým písmům a nastavením barev](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    > Aby bylo zajištěno, že výsledky získané dotazem jsou správné, může být užitečné použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> rozhraní k určení, zda je nutné vyprázdnit mezipaměť a aktualizovat před voláním metod načtení <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Získání informací o písmech a barvách pro obarvení textu](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Přístup k uloženým písmům a nastavením barev](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Postupy: přístup k vestavěným písmům a barevnému schématu](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Přehled písem a barev](../extensibility/font-and-color-overview.md)
