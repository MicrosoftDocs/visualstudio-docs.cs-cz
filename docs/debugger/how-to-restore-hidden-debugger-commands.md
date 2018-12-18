---
title: 'Postupy: obnovení skrytých příkazů ladicího programu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9ee37e72a52f866f5b67afaeacfd248628a3484
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176840"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Postupy: Obnovení skrytých příkazů ladicího programu
Při nastavování aplikace Visual Studio, zobrazí se výzva k výběru sada výchozích nastavení IDE pro primární programovací jazyk. Výchozí nastavení rozhraní IDE pro některé jazyky mohou skrývat určité příkazy ladicího programu.  
  
 Pokud chcete použít funkci ladicí program, který je skryt výchozího nastavení IDE, můžete přidat příkaz zpět do nabídky pomocí následujícího postupu.  
  
### <a name="to-restore-hidden-debugger-commands"></a>K obnovení skrytých příkazů ladicího programu  
  
1.  S projektem otevřeným v **nástroje** nabídky, klikněte na tlačítko **vlastní**.  
  
2.  V **vlastní** dialogové okno, klikněte na tlačítko **příkazy** kartu.  
  
3.  V **nabídek:** rozevíracího seznamu, vyberte **ladění** nabídky, která má obsahovat příkaz obnovený.  
  
4.  Klikněte na tlačítko **přidat příkaz...**  tlačítko.  
  
5.  V **přidat příkaz** , vyberte příkaz, který chcete přidat a klikněte na tlačítko **OK**.  
  
6.  Opakujte předchozí krok a přidejte další příkaz.  
  
7.  Klikněte na tlačítko **Zavřít** po dokončení přidání komentářů k nabídce.  
  
    > [!WARNING]
    >  Některé položky nabídky se zobrazí, pouze když ladicí program v konkrétní režimy, jako je například režimu běhu nebo režimu pozastavení. Položka, kterou jste přidali proto nemusí být ihned po dokončení těchto kroků.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Obnovení příkazů není k dispozici z dialogového okna Přizpůsobit  
 Některé příkazy, zejména těch, které jsou součástí hierarchické nabídky, nelze obnovit z **vlastní** dialogové okno. Chcete-li obnovit tyto příkazy, je nutné naimportovat nové kolekce nastavení prostředí IDE.  
  
#### <a name="to-import-new-ide-settings"></a>Chcete-li importovat nové nastavení prostředí IDE  
  
1.  Na **nástroje** nabídky, klikněte na tlačítko **nastavení importu a exportu**.  
  
2.  Na **Vítejte Průvodci importem a exportem nastavení** klikněte na **importovat vybrané nastavení prostředí**a potom klikněte na tlačítko **Další**.  
  
3.  Na **uložit aktuální nastavení** stránce, rozhodněte, jestli se mají uložit stávající nastavení a klikněte na **Další**.  
  
4.  Na **zvolte kolekce nastavení chcete importovat** stránce v části **výchozí nastavení** složky, zvolte kolekci nastavení pro vývoj, který obsahuje příkazy, které chcete použít. Pokud si nejste jisti kterou kolekci zvolte, zkuste **obecným vývojovým nastavením** nebo **Visual C++ – vývojové nastavení**, které poskytují největší příkazy ladicího programu.  
  
5.  Klikněte na tlačítko **Další**.  
  
6.  Na **zvolte nastavení pro import** stránce v části **možnosti**, ujistěte se, že **ladění** zaškrtnuto. Zrušte zaškrtnutí ostatních políček, pokud chcete importovat tato nastavení také.  
  
7.  Klikněte na tlačítko **Dokončit**.  
  
8.  Na **úplný Import** stránky, zkontrolujte všechny chyby spojené s obnovením vašeho nastavení v části **podrobnosti**.  
  
9. Klikněte na tlačítko **Zavřít**.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Základy ladicího programu](../debugger/getting-started-with-the-debugger.md)