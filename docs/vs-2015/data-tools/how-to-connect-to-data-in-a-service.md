---
title: 'Postupy: připojení k datům ve službě | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9bfa6c776e3a2137f751d4253feb0239811d95a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654693"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Postupy: Připojování k datům ve službě
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikaci připojíte k datům vráceným ze služby spuštěním [Průvodce konfigurací zdroje dat](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) a výběrem **služby** na stránce **Zvolte typ zdroje dat** .

 Po dokončení průvodce je do projektu přidán odkaz na službu, který je okamžitě k dispozici v [okně zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

> [!NOTE]
> Položky, které se zobrazí v okně **zdroje dat** , jsou závislé na informacích, které služba vrací. Některé služby nemusí poskytnout dostatek informací pro **Průvodce konfigurací zdroje dat** pro vytváření objektů s možností vazby. Například pokud služba vrátí netypové datové sady, po dokončení průvodce se nezobrazí žádné položky v **okně zdroje dat** . Důvodem je, že netypové datové sady neposkytují schéma, takže průvodce nemá k dispozici dostatek informací pro vytvoření zdroje dat.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-connect-your-application-to-a-service"></a>Připojení aplikace ke službě

1. V nabídce **data** klikněte na tlačítko **Přidat nový zdroj dat**.

2. Na stránce **Zvolte typ zdroje dat** vyberte **Služba** a pak klikněte na **Další**.

3. Zadejte adresu služby, kterou chcete použít, nebo klikněte na **Vyhledat** a vyhledejte služby v aktuálním řešení a potom klikněte na **Přejít**.

4. Volitelně lze nový **obor názvů** zadat místo výchozí hodnoty.

    > [!NOTE]
    > Kliknutím na tlačítko **Upřesnit** otevřete [dialogové okno Konfigurovat odkaz na službu](../data-tools/configure-service-reference-dialog-box.md).

5. Kliknutím na **OK** přidejte do svého projektu odkaz na službu.

6. Klikněte na tlačítko **Dokončit**.

     Zdroj dat se přidá do okna **zdroje dat** .

## <a name="next-steps"></a>Další kroky

#### <a name="to-add-functionality-to-your-application"></a>Přidání funkcí do aplikace

- Vyberte položku v okně **zdroje dat** a přetáhněte ji do formuláře pro vytvoření vázaných ovládacích prvků. Další informace najdete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Viz také
 [Vázání ovládacích prvků WPF ke službě WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [Windows Communication Foundation Services a WCF Data Services v aplikaci Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
