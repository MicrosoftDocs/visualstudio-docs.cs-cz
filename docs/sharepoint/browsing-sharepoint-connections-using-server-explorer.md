---
title: Procházení připojení služby SharePoint pomocí Průzkumník serveru | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: baf580ace98ab14032de1e9a3edf18af2b2cfee8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016344"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Procházení připojení služby SharePoint pomocí Průzkumník serveru
  Nyní můžete procházet místní připojení služby SharePoint v **Průzkumník serveru**. Pomocí této techniky můžete procházet komponenty webu služby SharePoint ve vašem systému. Komponenty SharePointového webu, jako jsou definice seznamů a typy obsahu, se zobrazí v uzlu s názvem **připojení služby SharePoint** ve stromovém zobrazení **Průzkumník serveru**. Chcete-li zobrazit **Průzkumník serveru**, na panelu nabídek vyberte možnost **Zobrazit**  >  **Průzkumník serveru**. Kromě zobrazení součástí webu služby SharePoint můžete odebrat položky, zobrazit jejich vlastnosti nebo aktualizovat stromové zobrazení pomocí příkazů v místní nabídce.

> [!IMPORTANT]
> Chcete-li procházet web služby SharePoint, musíte být správcem kolekce webů služby SharePoint a musíte mít aplikaci Visual Studio spuštěnou jako správce místního počítače. V opačném případě se web zobrazí v **Průzkumník serveru**, ale nemůžete rozbalit jeho uzel. Chcete-li ověřit, zda jste správcem kolekce webů, otevřete web ve webovém prohlížeči, otevřete nabídku **Akce webu** , zvolte možnost **oprávnění webového**serveru a poté na stránce **oprávnění: týmový web** zvolte příkaz **správce kolekce webů** ve skupině **Spravovat** na pásu karet. Pokud jste správcem kolekce webů, zobrazí se v textovém poli vaše jméno. Pokud se příkaz **správce kolekce webů** ve skupině Správa na pásu karet nezobrazí, nejste správcem této kolekce webů a musíte získat příslušná oprávnění od správce lokality.

## <a name="server-explorer-nodes"></a>Uzly Průzkumník serveru
 Všechny komponenty webu služby SharePoint jsou reprezentovány uzlem ve stromovém zobrazení **Průzkumník serveru** v části **připojení služby SharePoint**. Například výchozí weby služby SharePoint zahrnují typ obsahu s názvem diskuze, který představuje typ diskuze, který se zobrazí na stránce **diskuze** na webu služby SharePoint. Typ obsahu diskuze obsahuje několik polí. Chcete-li zobrazit tato pole v **Průzkumník serveru**, rozbalte uzel **ContentTypes** a potom uzel **diskuze** . V rámci tohoto pole jsou k dispozici několik uzlů, například body, předmět diskuze a název.

## <a name="node-shortcut-menu-commands"></a>Příkazy místní nabídky uzlu
 Každý uzel má místní nabídku, ke které máte přístup, kliknutím pravým tlačítkem myši na uzel nebo jeho výběrem a kliknutím na klávesy **SHIFT** + **F10** . Příkazy uzlu mohou zahrnovat následující:

|Název příkazu|Popis|
|------------------|-----------------|
|Aktualizovat|Aktualizuje stromové zobrazení tak, aby odrážel všechny změny, k nimž mohlo dojít od posledního zobrazení uzlu.|
|Odstranit|Odebere vybraný uzel ze stromového zobrazení. **Poznámka:**  Tento příkaz je povolen pouze v připojeních služby SharePoint uvedených v uzlu **připojení služby SharePoint** .|
|Vlastnosti|Zobrazí dostupné vlastnosti pro vybraný uzel v okně **vlastnosti** . Vlastnosti jsou jen pro čtení a ne každý uzel obsahuje přidružené vlastnosti.|
|Přidat připojení|Umožňuje zadat web služby SharePoint, který chcete procházet. K dispozici na uzlu **připojení služby SharePoint** a uzlech podřízených webů.|
|Zobrazit v prohlížeči|Zobrazí vybraný seznam ve webovém prohlížeči. Tento příkaz je k dispozici v některých seznamech pod uzlem **seznamy** , který je obsažen v **seznamech a knihovnách**.|

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: Přidání nebo odebrání připojení služby SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Popisuje kroky, které jsou požadovány pro přidání nového webu služby SharePoint do uzlu **připojení služby SharePoint** v **Průzkumník serveru**.|

## <a name="see-also"></a>Viz také
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
