---
title: 'Postupy: spuštění Průvodce nastavením TableAdapter | Dokumentace Microsoftu'
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
- TableAdapters, Configuration Wizard
- TableAdapter Configuration Wizard
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7f603789014239762f564c3b2391b99865d8f620
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261888"
---
# <a name="how-to-start-the-tableadapter-configuration-wizard"></a>Postupy: Spuštění Průvodce nastavením TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Průvodce nastavením TableAdapter** umožňuje vytvářet a upravovat objekty TableAdapter v datových sad silného typu. Průvodce vytvoří objekty TableAdapter založené na příkazy SQL, které zadáte v průvodci nebo na existující uložené procedury v databázi. Průvodce můžete také vytvořit nové uložené procedury v databázi, na základě příkazů SQL, které zadáte v průvodci.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-create-a-new-tableadapter"></a>Spusťte Průvodce konfigurací TableAdapter k vytvoření nového TableAdapter  
  
1.  Otevřete svou datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
    > [!NOTE]
    >  Pokud nemáte datové sady ve vašem projektu, přečtěte si téma [vytvoření a konfigurace datové sady](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
2.  Při vytváření nového TableAdapter. přetáhněte ji **TableAdapter** objektu z **datovou sadu** kartě **nástrojů** na **Návrhář Dataset**.  
  
3.  Na **vyberte datové připojení** stránce vyberte datové připojení ze seznamu aktuálně k dispozici připojení nebo vyberte **nové připojení** k vytvoření nového připojení.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-edit-an-existing-tableadapter"></a>Spusťte Průvodce konfigurací TableAdapter k úpravě stávajícího TableAdapter  
  
1.  Otevřete svou datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Klikněte pravým tlačítkem na TableAdapter v **Návrhář Dataset** a zvolte **konfigurovat**. Průvodce se otevře **vytvořit příkazy SQL** stránky nebo **příkazů vytvořit vazbu na existující uložené procedury** stránky, v závislosti na tom, jak TableAdapter původně nakonfigurován.  
  
3.  Dokončete průvodce.  
  
## <a name="see-also"></a>Viz také  
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)   
 [Vytváření a úpravy typovaných datových sad](../data-tools/creating-and-editing-typed-datasets.md)   
 [Přidat nové zdroje dat](../data-tools/add-new-data-sources.md)   
 [Postupy: připojení k datům v databázi](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Postupy: řazení a filtrování dat ADO.NET pomocí komponenty Windows Forms BindingSource](http://msdn.microsoft.com/library/6c206daf-d706-4602-9dbe-435343052063)   
 [Postupy: vytvoření vyhledávací tabulky s komponentou Windows Forms BindingSource](http://msdn.microsoft.com/library/622fce80-879d-44be-abbf-8350ec22ca2b)   
 [Návod: Zobrazování dat ve formuláři Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)