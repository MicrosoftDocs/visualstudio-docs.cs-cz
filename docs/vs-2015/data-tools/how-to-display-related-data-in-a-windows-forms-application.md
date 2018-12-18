---
title: 'Postupy: zobrazení souvisejících dat v Windows Forms aplikace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Windows Forms, displaying data
- displaying data, related data
- related data, displaying
- displaying tables, related data
- data [Windows Forms], displaying
- displaying table data
- data [Windows Forms], related
- displaying data on forms, related data
- displaying table information
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3fd7a29e1de66a5b5fd57dab1adbcf99128001ac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215459"
---
# <a name="how-to-display-related-data-in-a-windows-forms-application"></a>Postupy: Zobrazení souvisejících dat ve formulářové aplikaci Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete zobrazit související data přetažením položek, které sdílejí stejný uzel hlavní tabulky z [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) do formuláře. Například pokud máte datové zdroje, který má `Customers` tabulky a se souvisejícím `Orders` tabulky, zobrazí se obě tabulky jako uzly nejvyšší úrovně (ve stromovém zobrazení) v **zdroje dat** okna. Rozbalte `Customers` uzlu tak, aby viděli sloupce a si všimnete, že poslední sloupec v seznamu je rozbalitelný uzel představující `Orders` tabulky. Tento uzel představuje související objednávky zákazníka. To znamená, že pokud chcete vytvořit formulář, který vám umožní vybrat zákazníka a zobrazte seznam objednávek tohoto zákazníka, by bylo zapotřebí přetáhnout položky, které chcete zobrazit z této jedné hierarchie.  
  
 ![Okno zdroje dat zobrazuje vztah](../data-tools/media/datasources2.gif "DataSources2")  
Vytváření ovládacích prvků vázaných na data, které zobrazení souvisejících záznamů  
  
 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") video verzi tohoto tématu naleznete v tématu [jak I: aktualizace související tabulky](http://go.microsoft.com/fwlink/?LinkId=143527).  
  
### <a name="to-create-controls-that-display-related-records"></a>Chcete-li vytvořit ovládací prvky, které zobrazení souvisejících záznamů  
  
1.  Otevřete formulář v [Návrháře formulářů Windows](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
2.  Otevřít **zdroje dat** okna. Další informace najdete v tématu [postupy: otevření okna zdrojů dat](../data-tools/how-to-open-the-data-sources-window.md).  
  
3.  Rozbalte uzel představující nadřazené tabulky v relaci. (Nadřazená tabulka je tabulka na straně "1" vztah jeden mnoho.)  
  
4.  Přetáhněte všechny položky, které chcete zobrazit nadřazené tabulky v relaci z **zdroje dat** okna do formuláře.  
  
5.  Související podřízené tabulky se zobrazí jako rozbalovací uzly v dolní části seznamu sloupců v nadřazené tabulce. Přetáhněte položky, které chcete zobrazit související uzlu do formuláře.  
  
    > [!NOTE]
    >  Přetažením položky z uzly nejvyšší úrovně vytváří samostatnou nesouvisející [komponenty BindingSource](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9) , který není usnadnění procházení souvisejících záznamů. K vytvoření vazby souvisejících dat musíte vybrat tabulky od stejného uzlu hierarchický.  
  
## <a name="see-also"></a>Viz také  
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Návod: Zobrazování dat ve formuláři Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)   
 [Vytváření a úpravy typovaných datových sad](../data-tools/creating-and-editing-typed-datasets.md)   
 [Přidat nové zdroje dat](../data-tools/add-new-data-sources.md)   
 [Postupy: připojení k datům v databázi](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Postupy: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)