---
title: Přidat nová připojení | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 44146613fb43b6fc4269741ba09b94629f888d5f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673078"
---
# <a name="add-new-connections"></a>Přidání nových připojení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete testovat připojení k databázi nebo službě a prozkoumat obsah databáze a schémata pomocí **Průzkumník serveru**, **Průzkumníka cloudu**nebo **Průzkumník objektů systému SQL Server**. Funkčnost těchto oken se překrývá do určitého rozsahu. Základní rozdíly:

 Průzkumník serveru ve výchozím nastavení nainstalovány v aplikaci Visual Studio. Dá se použít k otestování připojení a zobrazení SQL Serverch databází, všech ostatních databází, které mají nainstalovaného poskytovatele ADO.NET, a některých služeb Azure. Zobrazuje také objekty nízké úrovně, jako jsou čítače výkonu systému, protokoly událostí a fronty zpráv. Pokud zdroj dat nemá žádného poskytovatele ADO.NET, nezobrazí se tady, ale můžete ho i nadále používat ze sady Visual Studio, a to tak, že se připojíte prostřednictvím kódu programu.

 Průzkumník cloudu nainstalujte toto okno ručně jako rozšíření sady Visual Studio, a to tak, že vyberete **nástroje**  > **rozšíření a aktualizace**  > **online**  > **Galerie sady Visual Studio**. Poskytuje specializované funkce pro zkoumání a připojování ke službám Azure.

 Průzkumník objektů systému SQL Server nainstalovány pomocí nástrojů SQL Server Data Tools a viditelné v nabídce **zobrazení** . Pokud tam není zobrazená, přejděte do části **programy a funkce** v Ovládacích panelech, najděte Visual Studio a pak vyberte **změnit** a znovu spusťte instalační program po zaškrtnutí políčka pro nástroje SQL Server Data Tools. Pomocí **Průzkumník objektů systému SQL Server** můžete zobrazit databáze SQL (pokud mají poskytovatele ADO.NET), vytvářet nové databáze, měnit schémata, vytvářet uložené procedury, načítat připojovací řetězce, zobrazovat data a další. Databáze SQL, které nemají nainstalovaného poskytovatele ADO.NET, se tady nezobrazí, ale můžete se k nim pořád připojit prostřednictvím kódu programu.

## <a name="add-a-connection-in-server-explorer"></a>Přidání připojení v Průzkumník serveru
 Chcete-li vytvořit připojení k databázi, klikněte na ikonu **Přidat připojení** v **Průzkumník serveru**nebo klikněte pravým tlačítkem myši v **Průzkumník serveru** v uzlu **datová připojení** a vyberte možnost **Přidat připojení**. Odtud se můžete připojit také k databázi na jiném serveru, službě SharePoint nebo službě Azure.

 ![Ikona Průzkumník serveru nového připojení](../data-tools/media/raddata-server-explorer-new-connection-icon.png "Ikona nového připojení raddata Průzkumník serveru")

 Tím se otevře dialogové okno **Přidat připojení** . Tady jsme zadali název instance SQL Server LocalDB.

 ![Přidat nové připojení](../data-tools/media/raddata-add-new-connection-dialog.png "Dialogové okno pro přidání nového připojení raddata")

## <a name="change-the-provider"></a>Změna zprostředkovatele
 Pokud zdroj dat není požadovaný, klikněte na tlačítko **změnit** a vyberte nový zdroj dat nebo nového poskytovatele dat ADO.NET. Nový poskytovatel může požádat o vaše přihlašovací údaje v závislosti na tom, jak jste ji nakonfigurovali.

 ![Změnit Zprostředkovatel dat AD0.NET](../data-tools/media/raddata-change-ad0-net-data-provider.png "raddata změny AD0.NET Zprostředkovatel dat")

## <a name="test-the-connection"></a>Otestování připojení
 Po výběru zdroje dat klikněte na tlačítko **Test připojení**. Pokud to nepomůže, budete muset řešit problémy na základě dokumentace od dodavatele.

 ![Testovat připojení](../data-tools/media/raddata-test-connection.png "raddata test připojení")

 Pokud je test úspěšný, jste připraveni vytvořit *zdroj dat*, což je Visual Studio Term, který se skutečně označuje jako *datový model* založený na podkladové databázi nebo službě.

## <a name="see-also"></a>Viz také
 [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
