---
title: 'Postupy: vytvoření vlastního textu značky | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ac2ad16c0e6a3e0a6c76e15ff6860838fa349c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893101"
---
# <a name="how-to-create-custom-text-markers"></a>Postupy: vytvoření vlastního textu značky
Pokud chcete vytvořit vlastní text značky zvýraznění nebo organizaci kódu, je nutné provést následující kroky:  
  
- Zaregistrujte nový text značky, tak, aby k němu mají přístup jiných nástrojů.  
  
- Zadejte výchozí implementace a konfigurace text značky.  
  
- Vytvoření služby, které lze použít s jinými procesy, aby používat text značky.  
  
  Podrobnosti o tom, jak použít text značky do oblasti kódu najdete v tématu [postupy: použití značek text](../extensibility/how-to-use-text-markers.md).  
  
## <a name="to-register-a-custom-marker"></a>Chcete-li zaregistrovat vlastní značky  
  
1. Vytvořte položku registru následujícím způsobem:  
  
    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\<verze > značky \Text Editor\External\\\<MarkerGUID >**  
  
    *\<MarkerGUID >* je `GUID` slouží k identifikaci značky přidávaný  
  
    `<Version>` je verze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], například 8.0  
  
    `<PackageGUID>` identifikátor GUID sady VSPackage implementuje objekt automatizace.  
  
   > [!NOTE]
   >  Kořenová cesta **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\<verze >** monitorconfigurationoverride lze přepsat náhradní root při inicializaci prostředí sady Visual Studio, pro další informace naleznete v tématu [Přepínače příkazového řádku](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Vytvořit čtyři hodnoty v rámci **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\<verze > \Text Editor\External značky\\\<MarkerGUID >**  
  
   -   (Výchozí)  
  
   -   Služba  
  
   -   displayName  
  
   -   Balíček  
  
   -   `Default` je typ REG_SZ volitelné položky. Pokud nastavíte hodnotu položky je řetězec obsahující některé užitečné identifikační informace, například "vlastní Text značky".  
  
   -   `Service` je typ REG_SZ položky obsahující řetězec GUID služby, která poskytuje vlastní text značky tím, že proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Formát je {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   -   `DisplayName` je typ REG_SZ položky obsahující ID prostředku názvu značky vlastní text. Formát je #YYYY.  
  
   -   `Package` je záznam obsahující typ REG_SZ `GUID` sady VSPackage, která poskytuje služby uvedené v části služby. Formát je {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
## <a name="to-create-a-custom-text-marker"></a>Chcete-li vytvořit vlastní text značky  
  
1.  Implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> rozhraní.  
  
     Implementace tohoto rozhraní definuje chování a vzhled typu vlastní značky.  
  
     Toto rozhraní je volána, když  
  
    1.  Uživatel spustí rozhraní IDE poprvé.  
  
    2.  Uživatel vybere **obnovit výchozí nastavení** tlačítko **písma a barvy** stránku vlastností v **prostředí** složku, v levém podokně  **Možnosti** dialogové okno získaných **nástroje** nabídky integrovaného vývojového prostředí.  
  
2.  Implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> metoda zadání která `IVsPackageDefinedTextMarkerType` implementace by měl být vrací na základě značky typu zadaný ve volání metody identifikátor GUID.  
  
     Prostředí volá tuto chvíli metoda první typ vaše vlastní značky se vytvoří a určuje identifikátor GUID určující typ vlastní značky.  
  
## <a name="to-proffer-your-marker-type-as-a-service"></a>Chcete-li nabídnout váš typ značky jako služba  
  
1.  Volání <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> metodu <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> je vrácena.  
  
2.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> metoda zadání identifikátoru GUID identifikující váš vlastní značky typu služby a poskytuje ukazatel na implementaci <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> rozhraní. Vaše <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementace by měla vrátit ukazatel na implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> rozhraní.  
  
     Jedinečný soubor cookie, který identifikuje vaši službu, je vrácena. Později můžete tento soubor cookie k odvolání vlastní značku služby typu při volání <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodu <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> rozhraní zadání této hodnoty souboru cookie.  
  
## <a name="see-also"></a>Viz také:  
 [Text značky pomocí starší verze rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Postupy: Přidání standardní text značky](../extensibility/how-to-add-standard-text-markers.md)   
 [Postupy: implementace označování chyb](../extensibility/how-to-implement-error-markers.md)   
 [Postupy: použití značek text](../extensibility/how-to-use-text-markers.md)