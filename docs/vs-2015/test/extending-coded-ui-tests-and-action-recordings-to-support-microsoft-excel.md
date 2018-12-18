---
title: Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b0f72a4-70ca-4e55-b236-2ea1034fd8a7
caps.latest.revision: 32
ms.author: gewarren
manager: douge
ms.openlocfilehash: 705604153a0f24eb7ae6b2ff5924a600ddbff54e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872977"
---
# <a name="extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel"></a>Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testovací rozhraní pro programové testy uživatelského rozhraní a zaznamenávání akcí nepodporuje každé uživatelské rozhraní. To nemusí podporovat konkrétní uživatelské rozhraní, které chcete testovat. Například nelze vytvořit okamžitě programový test uživatelského rozhraní nebo pro záznam akce [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] tabulky. Můžete však vytvořit vlastní rozšíření programového uživatelského rozhraní pro testování, která bude podporovat vaše konkrétní uživatelské rozhraní s využitím rozšíření programových testů uživatelského rozhraní. V následujícím tématu poskytuje příklad toho, jak rozšířit rozhraní podporuje vytváření programových testů UI a záznamů akcí pro [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Další informace o platformy, které jsou podporovány, naleznete v tématu [podporované konfigurace a platformy pro kódované testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).  
  
 **Požadavky**  
  
- Visual Studio Enterprise  
  
  Tato část představuje programového uživatelského rozhraní testu příponu, která můžete záznam a přehrávání testů sešitů aplikace Excel. Každá část tohoto rozšíření je vysvětleno v této části a v komentářích ke kódu pro vývojáře, kteří chtějí vytvořit právě takové rozšíření.  
  
  ![Architektura uživatelského rozhraní testu](../test/media/ui-testarch.png "UI_TestArch")  
  Přehled architektury  
  
## <a name="download-the-sample"></a>Stáhněte si ukázku  
 Ukázka se skládá ze čtyř projekty v `CodedUIExtensibilitySample.sln` řešení:  
  
- CodedUIextensibilitySample  
  
- ExcelCodedUIAddInHelper  
  
- ExcelUICommunicationHelper  
  
- SampleTestProject  
  
  Získat ukázky z tohoto [blogový příspěvek](http://go.microsoft.com/fwlink/?LinkID=185592).  
  
> [!NOTE]
>  Ukázka je určena pro použití s Microsoft Excel 2010. Ukázka může pracovat s jinými verzemi aplikace Microsoft Excel, ale není aktuálně podporován.  
  
## <a name="details-about-the-sample"></a>Podrobnosti o ukázku  
 Následující části obsahují informace o ukázce a jeho strukturu.  
  
### <a name="microsoft-excel-add-in-excelcodeduiaddinhelper"></a>Doplněk pro aplikaci Microsoft Excel: ExcelCodedUIAddinHelper  
 Tento projekt obsahuje doplněk, který běží v procesu Excelu. Zobrazit [doplňku ukázkové aplikace Excel pro programové testování uživatelského rozhraní](../test/sample-excel-add-in-for-coded-ui-testing.md) stručný přehled projektu doplňku.  
  
 Další informace najdete v tématu [názorný postup: Add-in vytvořit svůj první VSTO pro Excel](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f).  
  
### <a name="excel-ui-communication-exceluicommunicationhelper"></a>Uživatelské rozhraní Excelu komunikace: ExcelUIcommunicationHelper  
 Tento projekt obsahuje `IExcelUICommunication` rozhraní a třídy informace, které se používají k předávání dat mezi kódované UI Testing Framework a Excel. Další informace najdete v tématu [ukázka rozhraní Komunikátoru Excel](../test/sample-excel-communicator-interface.md).  
  
### <a name="coded-ui-test-extension-codeduiexentsibilitysample"></a>Rozšíření programového testu UI: CodedUIExentsibilitySample  
 Tento projekt obsahuje vlastní třídy, které se používají v testech z Excelového listu. Kód pro každý z těchto tříd je poměrně zřejmých. Však poskytujeme krátký popis každé vlastní třídy. Další informace najdete v tématu [ukázka programového uživatelského rozhraní testu rozšíření pro aplikaci Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
### <a name="deploying-your-add-in-and-extension"></a>Nasazování doplňky a rozšíření  
 Po vytvoření všechny projekty a objekty, spusťte zadaný `CopyDrop.bat` soubor jako správce. Tento soubor zkopíruje `ExcelCodedUIAddinHelper` soubory DLL a soubor PDB pro:  
  
 "`%CommonProgramFiles(x86)%\Microsoft Shared\VSTT\<version number>\UITestExtensionPackages\*.*`", kde číslo verze může být 11.0, 12,0 atd podle vaší verze sady Visual Studio.  
  
 `ExcelUICommunicationHelper` Soubory DLL a soubor PDB se zkopírují do `"%ProgramFiles(x86)%\Microsoft Visual Studio <version number>\Common7\IDE\PrivateAssemblies”`.  
  
 Možná budete muset nastavit přesná kopie cesty, ale žádná další instalace není nutná. Na 64bitovém počítači, použijte příkazový řádek sady Visual Studio Enterprise 32-bit ke spuštění `CopyDrop.bat` souboru.  
  
### <a name="testing-excel-with-the-sampletestproject"></a>Testování aplikace Excel s SampleTestProject  
 Spusťte test v zadané testovací projekt, který používá konkrétní verzi Excelu, nemusí mít, nebo vytvoříte projektu testu a zaznamenat test vlastní. Další informace najdete v tématu [vytváření programových testů UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Osvědčené postupy pro programové testy UI](../test/best-practices-for-coded-ui-tests.md)   
 [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)



