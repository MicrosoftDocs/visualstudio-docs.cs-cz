---
title: 'Postupy: ladění aplikace s částečnou důvěryhodností | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cce8cfcf57f956b5de16b72f7a275e1d629630
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782047"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Postupy: Ladění aplikace s částečnou důvěryhodností
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a konzolových aplikací.  
  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md) umožňuje snadno nasadit aplikace s částečnou důvěryhodností, které budou využívat [zabezpečení přístupu kódu](http://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) k omezení přístupu k prostředkům v počítači.  
  
 Ladění aplikace částečným vztahem důvěryhodnosti může být složité, protože aplikace s částečnou důvěryhodností máte oprávnění různé zabezpečení (a tedy chovat jinak) v závislosti na tom, kde jsou instalovány z. Pokud instalaci z Internetu bude mít aplikace s částečnou důvěryhodností několik oprávnění. Instalaci z místní intranet, bude mít další oprávnění a instalaci z místního počítače, bude mít úplná oprávnění. Také může mít vlastní zóny pomocí vlastních oprávnění. Budete muset ladění aplikace s částečnou důvěryhodností za některé nebo všechny z těchto podmínek. Naštěstí sady Visual Studio usnadňuje to i.  
  
 Než spustíte relaci ladění v sadě Visual Studio, můžete zónu, kterou chcete simulovat aplikace nainstalované z. Při spuštění ladění aplikace bude mít oprávnění pro aplikace s částečnou důvěryhodností nainstalovali z této zóny. To umožňuje zobrazit chování aplikace, jak se bude zobrazovat uživateli, který ji stáhnout z této zóny.  
  
 Pokud se aplikace pokusí provést akce, který nemá oprávnění pro, dojde k výjimce. Od tohoto okamžiku Pomocníka pro výjimky nabízí možnost přidávat další oprávnění, což umožňuje restartovat ladicí relaci s dostatečnými oprávněními, abyste zabránili problémům.  
  
 Později můžete vrátit a zobrazit oprávnění, která jste přidali během ladění. Pokud jste měli k přidání oprávnění při ladění, pravděpodobně znamená, že budete muset přidat uživatel vyjádřit souhlas výzvy v tomto okamžiku ve vašem kódu.  
  
> [!NOTE]
>  Ladicí program vizualizéry vyžadují, aby větší oprávnění než je povoleno hodnotou aplikace s částečnou důvěryhodností. Vizualizéry nenačte, když se zastaví v kódu s částečným vztahem důvěryhodnosti. Chcete-li ladit pomocí vizualizéru, musíte spustit kód s úplným vztahem důvěryhodnosti.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Chcete-li zvolit zóny pro vaši aplikaci částečným vztahem důvěryhodnosti  
  
1.  Z **projektu** nabídce zvolte _Projectname_**vlastnosti**.  
  
2.  V *Projectname* stránky vlastností, klikněte **zabezpečení** stránky.  
  
3.  Vyberte **povolení nastavení zabezpečení ClickOnce**.  
  
4.  V části **vaše aplikace bude provedena instalace ze zóny**, klikněte na rozevírací seznam a zvolte zónu, kterou chcete simulovat instaluje z aplikace.  
  
     **Oprávnění vyžadované aplikací** mřížky se zobrazí všechna dostupná oprávnění. Zaškrtávací políčko určuje oprávnění udělená aplikaci.  
  
5.  Pokud se zónu **(vlastní)**, vyberte správné vlastní nastavení v **nastavení** sloupec **oprávnění** mřížky.  
  
6.  Klikněte na tlačítko **OK** stránku vlastností zavřete.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Chcete-li přidat další oprávnění, když dojde k výjimce zabezpečení  
  
1.  **Pomocníka pro výjimky** dialogové okno se zprávou: **SecurityException – neošetřená.**  
  
2.  V **pomocníka pro výjimky** dialogovém okně **akce**, klikněte na tlačítko **oprávnění přidat do projektu**.  
  
3.  **Restartujte ladění** zobrazí se dialogové okno.  
  
    -   Pokud chcete restartovat ladicí relaci se nová oprávnění, klikněte na tlačítko **Ano**.  
  
    -   Pokud nechcete, aby se ještě restartovat, klikněte na tlačítko **ne**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Chcete-li zobrazit další oprávnění přidat při ladění  
  
1.  Z **projektu** nabídce zvolte _Projectname_**vlastnosti**.  
  
2.  V *Projectname* stránky vlastností, klikněte **zabezpečení** stránky.  
  
3.  Podívejte se na **oprávnění vyžadované aplikací** mřížky. Všechna další oprávnění, která jste přidali má dvě ikony v **zahrnuté** sloupec: normální značku zaškrtnutí, který všechny zahrnuté mít oprávnění a další ikony, který vypadá podobně jako bubliny obsahuje písmeno "i".  
  
4.  Svislý posuvník použít k zobrazení celého **oprávnění vyžadované aplikací** mřížky.  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)



