---
title: 'Postupy: použití dat do mezipaměti v režimu offline nebo na serveru'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a53b3539d71383d4fad95838250380c5849e8c5b
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254209"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Postupy: použití dat do mezipaměti v režimu offline nebo na serveru
  Můžete označit položku dat do mezipaměti v dokumentu, aby byla dostupná offline. To také umožňuje pro data v dokumentu, který má být manipulovat jiný kód, když je dokument uložen na serveru.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Můžete označit položku dat do mezipaměti, pokud položka dat je deklarovaný ve vašem kódu, nebo, pokud používáte <xref:System.Data.DataSet>, a to nastavením vlastnosti **vlastnosti** okno. Pokud jsou ukládání do mezipaměti položku dat, který není <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable>, ujistěte se, zda splňuje kritéria pro ukládat do mezipaměti v dokumentu. Další informace najdete v tématu [ukládat data do mezipaměti](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Datové sady vytvořené pomocí jazyka Visual Basic, které jsou označeny jako **mezipaměť** a **WithEvents** (včetně datové sady, které jsou přetažením z **zdroje dat** okno nebo **Sada nástrojů** mají **CacheInDocument** vlastnost nastavena na hodnotu **True**) mají podtržítkem předponu na jejich názvy v mezipaměti. Například pokud vytvoříte datové sady a pojmenujte ji **zákazníci**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> bude název **_Customers** v mezipaměti. Při použití <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pro přístup k této položky v mezipaměti, musíte zadat **_Customers** místo **zákazníci**.  
  
### <a name="to-cache-data-in-the-document-using-code"></a>Ukládat data do mezipaměti v dokumentu pomocí kódu  
  
1.  Deklarovat veřejné pole nebo vlastnost položky dat jako člena třídy položky hostitele ve vašem projektu, jako `ThisDocumen`t – třída v projektu aplikace Word nebo `ThisWorkbook` – třída v projektu aplikace Excel.  
  
2.  Použít <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atribut člen označit položku dat v datové mezipaměti dokumentu. Následující příklad se týká deklaraci pole pro tento atribut <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  Přidejte kód k vytvoření instance položky dat a pokud jsou k dispozici, načíst z databáze.  
  
     Datová položka načteny pouze při prvním vytvoření; následně mezipaměti zůstává dokumentu v platnosti a musíte napsat další kód jej aktualizovat.  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Pro ukládání do mezipaměti pomocí okna Vlastnosti datové sady v dokumentu  
  
1.  Přidejte datovou sadu do projektu pomocí nástrojů v návrháři Visual Studio, například přidáním zdroje dat pro váš projekt pomocí **zdroje dat** okno.  
  
2.  Vytvoření instance datové sady, pokud již máte jeden a vyberte instanci v návrháři.  
  
3.  V **vlastnosti** nastavte **CacheInDocument** vlastnost **True**.  
  
     Další informace najdete v tématu [vlastnosti v projektech Office](../vsto/properties-in-office-projects.md).  
  
4.  V **vlastnosti** nastavte **modifikátory** vlastnost **veřejné** (ve výchozím nastavení je **interní**).  
  
## <a name="see-also"></a>Viz také:  
 [Data do mezipaměti](../vsto/caching-data.md)   
 [Postupy: zdroji dat v dokumentu systému Office mezipaměti prostřednictvím kódu programu](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Postupy: mezipaměti data v dokumentu chráněném heslem](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Ukládání dat](/visualstudio/data-tools/saving-data)  
  
  