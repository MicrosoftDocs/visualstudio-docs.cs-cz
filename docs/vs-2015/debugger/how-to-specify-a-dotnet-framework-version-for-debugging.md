---
title: 'Postupy: určení verze .NET Framework pro ladění | Microsoft Docs'
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
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4c785c419ead31ad90e2b20ae7f48af778598bb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176555"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Postupy: Určení verze rozhraní .NET Framework pro ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]Ladicí program podporuje ladění starších verzí Microsoft i [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] aktuální verze. Pokud spustíte aplikaci ze sady Visual Studio, ladicí program může vždy identifikovat správnou verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] pro aplikaci, kterou ladíte. Pokud je aplikace již spuštěna a použijete **připojit k**, ladicí program nemusí vždy identifikovat starší verzi nástroje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . V takovém případě se zobrazí chybová zpráva s informacemi o tom,  
  
 Ladicí program provedl nesprávný předpoklad o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verzi, kterou vaše aplikace bude používat.  
  
 V těchto vzácných případech můžete nastavit klíč registru tak, aby označoval ladicí program, který má verze používat.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Určení verze .NET Framework pro ladění  
  
1. Vyhledejte v adresáři Windows\Microsoft.NET\Framework verze .NET Framework nainstalované na vašem počítači. Čísla verzí vypadají přibližně takto:  
  
     `V1.1.4322`  
  
     Identifikujte správné číslo verze a poznamenejte si ho.  
  
2. Spusťte **Editor registru** (Regedit).  
  
3. V **Editoru registru**otevřete složku HKEY_LOCAL_MACHINE.  
  
4. Přejít na: HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine \\ {449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Pokud klíč neexistuje, klikněte pravým tlačítkem HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine a klikněte na **nový klíč**. Pojmenujte nový klíč `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` .  
  
5. Po přechodu na {449EC4CC-30D2-4032-9256-EE18EB41B62B} se podívejte do sloupce **název** a vyhledejte klíč CLRVersionForDebugging.  
  
    1. Pokud klíč neexistuje, klikněte pravým tlačítkem na {449EC4CC-30D2-4032-9256-EE18EB41B62B} a pak klikněte na **Nová hodnota řetězce**. Pak klikněte pravým tlačítkem na novou řetězcovou hodnotu, klikněte na **Přejmenovat**a zadejte `CLRVersionForDebugging` .  
  
6. Dvakrát klikněte na **CLRVersionForDebugging**.  
  
7. Do pole **Upravit řetězec** zadejte .NET Framework číslo verze do pole **hodnota** . Příklad: V 1.1.4322  
  
8. Klikněte na **OK**.  
  
9. Zavřete **Editor registru**.  
  
     Pokud se vám při zahájení ladění stále zobrazí chybová zpráva, ověřte, že jste v registru zadali číslo verze správně. Ověřte také, že používáte verzi, kterou [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] podporuje aplikace Visual Studio. Ladicí program je kompatibilní s aktuální verzí .NET Framework a předchozími verzemi, ale nemusí být dopředný kompatibilní s budoucími verzemi.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
