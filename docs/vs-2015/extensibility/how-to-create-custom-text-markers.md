---
title: 'Postupy: vytváření vlastních značek textu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780962"
---
# <a name="how-to-create-custom-text-markers"></a>Postupy: Vytvoření vlastních textových značek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li vytvořit vlastní značku textu pro zdůraznění nebo uspořádání kódu, je nutné provést následující kroky:  
  
- Zaregistruje novou značku textu, aby k nim měli přístup ostatní nástroje.  
  
- Zadejte výchozí implementaci a konfiguraci značky text.  
  
- Vytvoření služby, kterou mohou používat jiné procesy k používání značky text  
  
  Podrobnosti o tom, jak použít značku textu pro oblast kódu, naleznete v tématu [How to: use text Marks](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Registrace vlastní značky  
  
1. Vytvořte položku registru následujícím způsobem:  
  
    HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text značky Editor\External\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID></em>slouží `GUID` k identifikaci přidávané značky.  
  
    *\<Version>* je verze, například [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 8,0  
  
    *\<PackageGUID>* je identifikátor GUID VSPackage implementující automatizační objekt.  
  
   > [!NOTE]
   > Kořenovou cestu HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* lze přepsat alternativním kořenem při inicializaci prostředí sady Visual Studio. Další informace naleznete v tématu [přepínače příkazového řádku](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Vytvořit čtyři hodnoty pod HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text značky Editor\External\\*\<MarkerGUID>*  
  
   - (Výchozí)  
  
   - Služba  
  
   - DisplayName  
  
   - Balíček  
  
   - `Default` je volitelná položka typu REG_SZ. Při nastavení je hodnota položky řetězec, který obsahuje některé užitečné identifikační informace, například vlastní značku textu.  
  
   - `Service` je položka typu REG_SZ obsahující řetězec GUID služby, který poskytuje vlastní značku textu Proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> . Formát je {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   - `DisplayName` je položka typu REG_SZ obsahující ID prostředku názvu vlastní značky textu. Formát je #YYYY.  
  
   - `Package` je zadání typu REG_SZ obsahujícího `GUID` VSPackage, který poskytuje službu uvedenou v části služba. Formát je {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Vytvoření vlastní značky textu  
  
1. Implementujte rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     Vaše implementace tohoto rozhraní definuje chování a vzhled vlastního typu značky.  
  
     Toto rozhraní se volá, když  
  
    1. Uživatel poprvé spustí integrované vývojové prostředí (IDE).  
  
    2. Uživatel vybere tlačítko **Obnovit výchozí** na stránce vlastností **písma a barvy** ve složce prostředí, která je umístěna v levém podokně dialogového okna **Možnosti** , které je získáno z nabídky **nástroje** v integrovaném vývojovém **prostředí** (IDE).  
  
2. Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> metodu a určete, která `IVsPackageDefinedTextMarkerType` implementace má být vrácena na základě identifikátoru GUID typu značky zadaného ve volání metody.  
  
     Prostředí volá tuto metodu při prvním vytvoření vlastního typu značky a určuje identifikátor GUID identifikující typ vlastní značky.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Nabídnout typu značky jako služby  
  
1. Zavolejte <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> metodu pro <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> .  
  
     Ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> je vrácen.  
  
2. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> metodu, zadáním identifikátoru GUID identifikující vaši vlastní typ značky a poskytněte ukazatel na implementaci <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> rozhraní. Vaše <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementace by měla vrátit ukazatel na vaši implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> rozhraní.  
  
     Jedinečný soubor cookie identifikující, že vaše služba je vrácena. Později můžete tento soubor cookie použít k odvolání vlastní služby typu značky voláním <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metody rozhraní, které <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Určuje tuto hodnotu souboru cookie.  
  
## <a name="see-also"></a>Viz také  
 [Používání textových značek se starší verzí rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Postupy: Přidání standardních značek textu](../extensibility/how-to-add-standard-text-markers.md)   
 [Postupy: implementace značek chyb](../extensibility/how-to-implement-error-markers.md)   
 [Postupy: Použití textových značek](../extensibility/how-to-use-text-markers.md)
