---
title: Vytváření balíčků řešení služby SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 87b80d7c607cf4de686e601263bcb67dcc2f92ae
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326849"
---
# <a name="create-sharepoint-solution-packages"></a>Vytváření balíčků řešení služby SharePoint
  Pomocí návrháře balíčků, můžete vytvořit a upravit balíčky pro nasazení. Například můžete přidat položky projektu služby SharePoint a funkce, obnovit server služby IIS, nastavte obory aktivace funkce a identifikovat funkcí. Návrhář také generuje manifest, soubor XML, který popisuje každý balíček.  
  
## <a name="packaging-tools"></a>Nástroje pro balení
 Můžete použít **návrháře balíčků** přizpůsobení balíčku a generování manifestu. Můžete zahrnout položky projektu služby SharePoint, nakonfigurovat, jestli webový server by měl resetování a nastavte typ serveru nasazení. Další informace najdete v tématu [postupy: Přidání nebo odebrání funkcí a položek z balíčku pomocí návrháře balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 Alternativně můžete použít **Průzkumníku balíčků** k úpravě funkcí a položek v souboru balíčku (*WSP*). Další informace najdete v tématu [postupy: Přidání nebo odebrání funkcí a položek z balíku pomocí Průzkumníku balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 Visual Studio a nástroje MSBuild můžete použít k vytvoření balíčku (*WSP*) soubory k nasazení řešení služby SharePoint. Tento proces generuje manifest soubory potřebné pro nasazení služby SharePoint. Další informace najdete v tématu [postupy: vytvoření balíčku řešení služby SharePoint pomocí úloh nástroje MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Možnosti návrháře balíčků
 Následující tabulka uvádí vlastnosti lze přizpůsobit v SharePoint balíčky s **návrháře balíčků**.  
  
|Vlastnosti návrháře balíčků|Popis výchozí nastavení|  
|-------------------------------|------------------------------------|  
|Název|Požadováno. Výchozí název balíčku je nastaven *ProjectName*.|  
|Resetovat webový server|Volitelné. Vyberte, pokud chcete restartovat server po *WSP* soubor je nainstalován na serveru SharePoint.|  
|Typ nasazení serveru|Požadováno. Ve výchozím nastavení je ApplicationServer hodnotu oboru.<br /><br /> ApplicationServer: Popisuje serveru, který je hostitelem služby.<br /><br /> WebFrontEnd: Popisuje serveru, který je hostitelem webové stránky.|  
|Položky v řešení|SharePoint – položky projektu a funkce, které mohou být přidány do balíčku.|  
|Položky v balíčku|Volitelné. Všechny položky služby SharePoint a funkce, které chcete nasadit do balíčku.|  
  
## <a name="configure-the-packaging-process"></a>Konfigurace vytváření balíčku
 Až budete vyvíjet řešení služby SharePoint v sadě Visual Studio, můžete přizpůsobit, jak spojených projektů.  
  
 V následující tabulce jsou uvedeny dva cíle MSBuild, které můžete použít k přizpůsobení jak *WSP* soubor je vytvořen.  
  
|Cíl|Popis|  
|------------|-----------------|  
|BeforeLayout|Cíl, který provádí úlohy bezprostředně před soubory se zkopírují do zprostředkující adresáře. Můžete změnit soubory, před vytvořením souboru balíčku (*WSP*).|  
|AfterLayout|Cíl, který provádí úlohy ihned po soubory se zkopírují do zprostředkující adresáře.|  
  
 Další informace najdete [postupy: přizpůsobení balíčku řešení služby SharePoint pomocí cílů nástroje MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Architektura balení
 Následující kroky dojít, když vytvoříte balíček služby SharePoint (*WSP*) v sadě Visual Studio.  
  
1.  Funkce a balíčky se ověří a ujistěte se, zda je správný fyzické a sémantický strukturu balíčku.  
  
2.  Jsou uvedené funkce, položky projektu a soubory balíčku v balíčku. Soubory manifestu pro balíčky a funkce jsou transformovány zahrnout všechny potřebné informace pro nasazení a aktivaci. Tokeny jsou nahrazeny plně kvalifikovaný hodnota.  
  
3.  Přizpůsobitelné cíle BeforeLayout MSBuild se provádí. Můžete vytvořit tento krok, aby veškeré vlastní úpravy balíček před *WSP* soubor je vytvořen.  
  
4.  Výčtové soubory se zkopírují do zprostředkující adresáře.  
  
5.  Přizpůsobitelné cíle AfterLayout MSBuild provádí. Můžete vytvořit tento krok, aby veškeré vlastní úpravy balíček před *WSP* soubor je vytvořen.  
  
6.  Soubory v adresáři zprostředkující budou přidány do *WSP* souboru.  
  
## <a name="package-folder-structure"></a>Struktura složek balíčku
 Když balíček projektu služby SharePoint *WSP* se vám v vytvoří soubor *SolutionFolder\bin\\\<BuildConfiguration >* složky. Například, pokud je vaše řešení v *C:\Visual Studio 2013\Projects\ListDefinition1* a vaše konfigurace sestavení nastavená na vydání *WSP* soubor je umístěný ve *2013\ C:\Visual Studio Projects\ListDefinition1\bin\Release*.  
  
## <a name="see-also"></a>Viz také:
 [Postupy: přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Postupy: Přidání nebo odebrání funkcí a položek z balíčku pomocí návrháře balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Postupy: vytvoření balíčku řešení služby SharePoint pomocí úloh nástroje MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Postupy: vytvoření balíčku řešení služby SharePoint pomocí úloh nástroje MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Postupy: přizpůsobení balíčku řešení služby SharePoint pomocí cílů nástroje MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
 
