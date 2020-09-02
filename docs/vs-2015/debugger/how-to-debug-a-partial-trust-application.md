---
title: 'Postupy: ladění aplikace s částečnou důvěryhodností | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 030fef750cc1e0f0932de32fca1a0ffef56bc8f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704487"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Postupy: Ladění aplikace s částečnou důvěryhodností
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a konzolové aplikace.  
  
 [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md) usnadňuje nasazení částečně důvěryhodných aplikací, které využívají [zabezpečení přístupu kódu](https://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) k omezení přístupu k prostředkům v počítači.  
  
 Ladění aplikace s částečným vztahem důvěryhodnosti může být výzvou, protože aplikace s částečným vztahem důvěryhodnosti mají odlišná oprávnění zabezpečení (a proto se chovají jinak) v závislosti na tom, odkud jsou nainstalovány. Při instalaci z Internetu bude mít aplikace s částečnou důvěryhodností jenom několik oprávnění. Pokud je aplikace nainstalovaná z místního intranetu, bude mít další oprávnění a pokud je nainstalovaná z místního počítače, bude mít úplná oprávnění. Můžete mít také vlastní zóny s vlastními oprávněními. Je možné, že bude nutné ladit aplikace s částečným vztahem důvěryhodnosti v rámci kterékoli nebo všech těchto podmínek. Díky tomu je Visual Studio také snadné.  
  
 Než začnete ladit relaci v aplikaci Visual Studio, můžete zvolit zónu, ze které chcete simulovat aplikaci nainstalovanou. Když začnete s laděním, aplikace bude mít oprávnění, která jsou vhodná pro aplikace s částečným vztahem důvěryhodnosti nainstalovanou z této zóny. To vám umožní zobrazit chování aplikace, jak by se zobrazilo uživateli, který si ho stáhl z této zóny.  
  
 Pokud se aplikace pokusí provést akci, ke které nemá oprávnění, dojde k výjimce. V tomto okamžiku Pomocník pro výjimky vám dává možnost přidat další oprávnění, což vám umožní restartovat relaci ladění s dostatečnými oprávněními, abyste se vyhnuli problému.  
  
 Později se můžete vrátit a podívat se, jaká oprávnění jste přidali během ladění. Pokud jste museli během ladění přidat oprávnění, pravděpodobně to znamená, že v tomto okamžiku v kódu musíte přidat výzvu k zadání souhlasu uživatele.  
  
> [!NOTE]
> Nástroje pro vizualizace ladicího programu vyžadují větší oprávnění, než povoluje aplikace s částečnou důvěryhodností. Když zastavíte kód s částečnou důvěryhodností, vizualizace se nenačte. Chcete-li provést ladění pomocí vizualizér, je nutné spustit kód s úplným vztahem důvěryhodnosti.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Výběr zóny pro aplikaci s částečným vztahem důvěryhodnosti  
  
1. V nabídce **projekt** vyberte**vlastnosti** _ProjectName_.  
  
2. Na stránkách vlastností *ProjectName* klikněte na stránku **zabezpečení** .  
  
3. Vyberte **Povolit nastavení zabezpečení ClickOnce**.  
  
4. V části **zóna, ze které se aplikace nainstaluje**, klikněte na rozevírací seznam a vyberte zónu, ze které chcete aplikaci nainstalovanou simulovat.  
  
     **Oprávnění vyžadovaná** mřížkou aplikace zobrazují všechna dostupná oprávnění. Značka zaškrtnutí označuje oprávnění udělená vaší aplikaci.  
  
5. Pokud se zvolená zóna **(vlastní)**, vyberte ve sloupci **Nastavení** v mřížce **oprávnění** správné vlastní nastavení.  
  
6. Kliknutím na tlačítko **OK** zavřete stránky vlastností.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Přidání dalšího oprávnění, když dojde k výjimce zabezpečení  
  
1. Zobrazí se dialogové okno **Pomocník pro výjimky** s touto zprávou: **SecurityException bylo neošetřené.**  
  
2. V dialogovém okně **Pomocník pro výjimky** v části **Akce**klikněte na **Přidat oprávnění k projektu**.  
  
3. Zobrazí se dialogové okno **restartovat ladění** .  
  
    - Pokud chcete spustit relaci ladění s novým oprávněním, klikněte na **Ano**.  
  
    - Pokud se ještě nechcete restartovat, klikněte na **ne**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Zobrazení dalších oprávnění přidaných během ladění  
  
1. V nabídce **projekt** vyberte**vlastnosti** _ProjectName_.  
  
2. Na stránkách vlastností *ProjectName* klikněte na stránku **zabezpečení** .  
  
3. Podívejte se na **oprávnění požadovaná** v mřížce aplikace. Všechna dodatečná oprávnění, která jste **přidali, mají ve sloupci include** dvě ikony: normální značka zaškrtnutí, která všechna zahrnutá oprávnění mají, a další ikonu, která vypadá jako bublina obsahující písmeno "i".  
  
4. Pomocí svislého posuvníku můžete zobrazit všechna **oprávnění požadovaná** mřížkou aplikace.  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)
