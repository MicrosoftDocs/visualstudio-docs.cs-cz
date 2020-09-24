---
title: 'Postupy: Obnovení skrytých příkazů ladicího programu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 297be3a3a4ad3c70ad28c627d5dc8d64c6ba1c7a
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2020
ms.locfileid: "64830868"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Postupy: Obnovení skrytých příkazů ladicího programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při nastavování aplikace Visual Studio budete požádáni o výběr sady výchozích nastavení IDE pro primární programovací jazyk. Výchozí nastavení IDE pro některé jazyky mohou skrýt určité příkazy ladicího programu.  
  
 Pokud chcete použít funkci ladicího programu, která je skrytá ve výchozím nastavení IDE, můžete příkaz přidat zpátky do nabídky pomocí následujícího postupu.  
  
### <a name="to-restore-hidden-debugger-commands"></a>Postup obnovení skrytých příkazů ladicího programu  
  
1. Otevřete-li projekt, v nabídce **nástroje** klikněte na možnost **přizpůsobit**.  
  
2. V dialogovém okně **přizpůsobit** klikněte na kartu **příkazy** .  
  
3. V **panelu nabídek:** vyberte nabídku **ladění** , kterou chcete obnovit.  
  
4. Klikněte na **příkaz Přidat...** .  
  
5. V okně **Přidat** vyberte příkaz, který chcete přidat, a klikněte na **OK**.  
  
6. Opakujte předchozí krok a přidejte další příkaz.  
  
7. Po dokončení přidávání příkazů do nabídky klikněte na **Zavřít** .  
  
    > [!WARNING]
    > Některé položky nabídky se zobrazí pouze v případě, že je ladicí program v konkrétních režimech, jako je režim běhu nebo režim přerušení. Proto se položka, kterou jste přidali, nemusí hned po dokončení těchto kroků zobrazit okamžitě.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Obnovení příkazů, které nejsou k dispozici v dialogovém okně přizpůsobit  
 Některé příkazy, zejména ty, které se nacházejí v hierarchických nabídkách, nelze obnovit v dialogovém okně **přizpůsobit** . Chcete-li obnovit tyto příkazy, je nutné importovat novou kolekci nastavení IDE.  
  
#### <a name="to-import-new-ide-settings"></a>Import nového nastavení IDE  
  
1. V nabídce **nástroje** klikněte na položku **Nastavení importu a exportu**.  
  
2. Na stránce **Vítá vás Průvodce importem a exportem nastavení** klikněte na **Importovat vybrané nastavení prostředí**a pak klikněte na **Další**.  
  
3. Na stránce **Uložit aktuální nastavení** rozhodněte, zda chcete uložit existující nastavení, a poté klikněte na tlačítko **Další**.  
  
4. Na stránce **zvolit kolekci nastavení k importu** vyberte v části **výchozí nastavení** složku nastavení pro vývoj, která obsahuje příkazy, které chcete použít. Pokud si nejste jisti, kterou kolekci si vybrat, zkuste **Obecné vývojové nastavení** nebo **Visual C++ vývojové nastavení**, které poskytuje většinu příkazů ladicího programu.  
  
5. Klikněte na **Next** (Další).  
  
6. Na stránce **zvolit nastavení pro import** v části **Možnosti**zkontrolujte, zda je vybráno **ladění** . Pokud tato nastavení nechcete importovat, zrušte zaškrtnutí těchto políček.  
  
7. Klikněte na **Finish** (Dokončit).  
  
8. Na stránce **importovat dokončení** zkontrolujte všechny chyby spojené s resetováním nastavení v části **Podrobnosti**.  
  
9. Klikněte na **Zavřít**.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)
