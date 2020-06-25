---
title: 'Postupy: Připojování k datům ve službě'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0b49840a2190abfd223edf5643b8d70da1a59d6b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282225"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Postupy: připojení k datům ve službě

Aplikaci připojíte k datům vráceným ze služby spuštěním [Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png) a výběrem **služby** na stránce **Zvolte typ zdroje dat** .

Po dokončení průvodce je do projektu přidán odkaz na službu, který je okamžitě k dispozici v [okně zdroje dat](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Položky, které se zobrazí v okně **zdroje dat** , jsou závislé na informacích, které služba vrací. Některé služby nemusí poskytnout dostatek informací pro **Průvodce konfigurací zdroje dat** pro vytváření objektů s možností vazby. Například pokud služba vrátí netypové datové sady, nezobrazí se žádné položky v okně **zdroje dat** po dokončení průvodce. Důvodem je, že netypové datové sady neposkytují schéma, takže průvodce nemá k dispozici dostatek informací pro vytvoření zdroje dat.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Připojení aplikace ke službě

1. V nabídce **data** klikněte na tlačítko **Přidat nový zdroj dat**.

2. Na stránce **Zvolte typ zdroje dat** vyberte **Služba** a pak klikněte na **Další**.

3. Zadejte adresu služby, kterou chcete použít, nebo klikněte na **Vyhledat** a vyhledejte služby v aktuálním řešení a potom klikněte na **Přejít**.

4. Volitelně můžete zadat nový **obor názvů** místo výchozí hodnoty.

    > [!NOTE]
    > Kliknutím na tlačítko **Upřesnit** otevřete [dialogové okno Konfigurovat odkaz na službu](../data-tools/configure-service-reference-dialog-box.md).

5. Kliknutím na **OK** přidejte do svého projektu odkaz na službu.

6. Klikněte na **Finish** (Dokončit).

     Zdroj dat se přidá do okna **zdroje dat** .

## <a name="next-steps"></a>Další kroky

Chcete-li do aplikace přidat funkce, vyberte položku v okně **zdroje dat** a přetáhněte ji do formuláře pro vytvoření vázaných ovládacích prvků. Další informace najdete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků WPF k datové službě WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Služby Windows Communication Foundation Services a WCF Data Services v aplikaci Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
