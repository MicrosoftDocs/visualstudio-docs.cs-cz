---
title: Vyvolání ladicího programu pro programovací model Windows Workflow Foundation (starší verze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcceca362f3c2a891d36f8f4e8071d0e35c8f164
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658983"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Vyvolání ladicího programu sady Visual Studio pro programovací model Windows Workflow Foundation (starší verze)
Toto téma popisuje, jak pomocí ladicího programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ladit aplikace [!INCLUDE[wf](../includes/wf-md.md)] ve starší verzi [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Starší verze [!INCLUDE[wfd2](../includes/wfd2-md.md)] použijte, pokud potřebujete cílit buď na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)], nebo na [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Obecně ladíte starší pracovní postupy stejně jako při ladění programů napsaných v jiných programovacích jazycích sady Visual Studio. @No__t_0 ladicí program můžete spustit pro programovací model Windows Workflow Foundation následujícími způsoby:

- V nabídce **ladění** vyberte možnost **připojit k procesu** a vyberte spuštěnou instanci pracovního postupu z dostupných procesů.

- Stiskněte klávesu **F5** ke spuštění instance pracovního postupu nebo ke spuštění i po dosažení zarážky.

## <a name="stepping-through-code"></a>Krokování prostřednictvím kódu
 Ladicí program podporuje jeden z nejběžnějších postupů ladění, krokování, které spouští kód po jednotlivých řádcích. Existují tři příkazy pro krokování kódu:

- **Krok**dovnitř: můžete krokovat s aktivitou pomocí **klávesy F11**. Ladicí program popisuje všechny definované obslužné rutiny. Pokud není definována žádná obslužná rutina, můžete krokovat s aktivitou nebo se složenými aktivitami, které obsahují další aktivity, a krokovat s první vykonávanou aktivitou. Krokování obslužných rutin kódu z návrháře není podporováno pro následující aktivity: **IfElseActivity**, **Aktivita typu WhileActivity**, **aktivitou skupiny ConditionedActivityGroup**nebo **Aktivita ReplicatorActivity**. Chcete-li ladit obslužné rutiny spojené s těmito aktivitami, je nutné do kódu umístit explicitní zarážky.

- **Krok ven**: můžete se Krokovat s aktivitou pomocí **SHIFT + F11**. Krokování mimo aktivitu spustí aktuální aktivitu a všechny její aktivity na stejné úrovni jako dokončené. Ladicí program se pak rozdělí na nadřazený objekt aktuální aktivity. Při rozkrokování z obslužné rutiny kódu se ladicí program ukončí u aktivity, ke které je přidružena obslužná rutina.

- **Krok za krokem**: můžete krokovat aktivitu pomocí **F10**. Při krokování nad složenou aktivitou. ladicí program se přerušuje u prvního spustitelného prvku složené aktivity. Při rozkrokování mimo nesložené, jako je aktivita **CodeActivity** , ladicí program spustí aktivitu a její přidružené obslužné rutiny a přeruší na další aktivitu. Pokud je spuštěná aktivita poslední podřízená aktivita v složené aktivitě, potom po provedení se ladicí program ukončí u nadřazené aktivity.

## <a name="attaching-to-a-process"></a>Připojení k procesu
 Chcete-li ladit pracovní postup připojením k procesu, vyberte možnost dostupný proces ze seznamu **procesy k** dispozici v dialogovém okně **připojit k procesu** . Pokud se **automaticky: kód workflowu** v textovém poli **připojit k** nezobrazuje, klikněte na **Vybrat**. V dialogovém okně **Vybrat typ kódu** klikněte na možnost **ladit tyto typy kódu** a vyberte možnost **pracovní postup**. Pak klikněte na **OK** a pak klikněte na **připojit**.

## <a name="debugging-with-f5"></a>Ladění pomocí F5
 Pokud je hostitelská aplikace pracovního postupu a knihovna DLL pracovního postupu umístěn v různých projektech sady Visual Studio, například při použití knihovny aktivity pracovního postupu, je nutné nastavit projekt knihovny DLL pracovního postupu jako projekt po spuštění řešení sady Visual Studio pro ladění pracovního postupu. pomocí **F5**. Musíte také nastavit cestu k hostitelské aplikaci v projektu knihovny DLL pracovního postupu pro vlastnost **spustit externí program** .

 Chcete-li nastavit projekt po spuštění v Průzkumník řešení, klikněte pravým tlačítkem myši na název projektu a vyberte **nastavit jako spouštěný projekt**. Chcete-li nastavit cestu k hostiteli ve vlastnosti **spustit externí program** , poklikejte na uzel **vlastností** projektu pracovního postupu v Průzkumník řešení a vyberte kartu **ladit** . V části **Spustit akci**vyberte **spustit externí program** a zadejte cestu k souboru. exe, který je hostitelem pracovního postupu, který chcete ladit.

 Pokud je hostitelská aplikace nastavena jako spouštěný projekt, je pro ladění vyvolána pouze ladicí program sady Visual Studio. [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] ladicí program pro programovací model Windows Workflow Foundation není vyvolán. Pokud je použit ladicí program sady Visual Studio, C# jsou dosaženy pouze nebo Visual Basic zarážky kódu; zarážky nastavené v Návrháři pracovních postupů nejsou k dispozice. Například zarážka, kterou jste nastavili u aktivity <xref:System.Workflow.Activities.ParallelActivity> v návrháři, je dosaženo, pokud je použit ladicí program [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] pro programovací model Windows Workflow Foundation, ale ne při použití ladicího programu sady Visual Studio.

## <a name="see-also"></a>Viz také
 [Postupy: nastavení zarážek v pracovních postupech (starší verze)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [ladění starších verzí pracovních postupů](../workflow-designer/debugging-legacy-workflows.md)