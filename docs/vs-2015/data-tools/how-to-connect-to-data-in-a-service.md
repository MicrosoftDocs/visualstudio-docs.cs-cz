---
title: 'Postupy: připojení k datům ve službě | Dokumentace Microsoftu'
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
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce851a864dd11759c36c7ae6cb275e9e71cd11a1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301792"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Postupy: Připojování k datům ve službě
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Připojení vaší aplikace s daty vrácenými ze služby spuštěním [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) a vyberete **služby** na **zvolte typ zdroje dat**stránky.  
  
 Po dokončení průvodce se odkaz na službu se přidá do vašeho projektu a je okamžitě k dispozici v [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
> [!NOTE]
>  Položky, které se zobrazují v **zdroje dat** okna jsou závislé na informace, které služba vrací. Některé služby nemusí poskytnout dostatek informací, **Průvodce konfigurací zdroje dat** vytvořil objekty. Například pokud služba vrátí netypovou datovou sadu, pak se neobjeví žádné položky v **okna zdroje dat** po dokončení průvodce. Je to proto netypové datové sady neposkytují schéma, proto Průvodce nemá dostatek informací pro vytvoření zdroje dat.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Pro připojení aplikace ke službě  
  
1.  Na **Data** nabídky, klikněte na tlačítko **přidat nový zdroj dat**.  
  
2.  Vyberte **služby** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.  
  
3.  Zadejte adresu služby, kterou chcete použít, nebo klikněte na tlačítko **Discover** vyhledejte služby v aktuálním řešení a potom klikněte na **Přejít**.  
  
4.  Volitelně můžete nové **Namespace** lze zadat místo výchozí hodnotu.  
  
    > [!NOTE]
    >  Klikněte na tlačítko **Upřesnit** otevřít [konfigurace Service Reference Dialog Box](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Klikněte na tlačítko **OK** přidáte odkaz na službu do projektu.  
  
6.  Klikněte na tlačítko **Dokončit**.  
  
     Zdroj dat je přidaný do **zdroje dat** okna.  
  
## <a name="next-steps"></a>Další kroky  
  
#### <a name="to-add-functionality-to-your-application"></a>Přidání funkčnosti do aplikace  
  
-   Vyberte položku **zdroje dat** okno a přetáhněte jej na formulář pro vytvoření vazby ovládacích prvků. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků WPF k datové služby WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

