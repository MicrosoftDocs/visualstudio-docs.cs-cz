---
title: 'Návod: Vytvoření jednoduché služby WCF v model Windows Forms | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 366567a13ad23ab19ffd88f19997b92025abe952
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671077"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Návod: Vytvoření jednoduché služby WCF v model Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak vytvořit jednoduchou službu [!INCLUDE[vsindigo](../includes/vsindigo-md.md)], otestovat ji a pak k ní přistupovat z aplikace model Windows Forms.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="creating-the-service"></a>Vytvoření služby

#### <a name="to-create-a-wcf-service"></a>Vytvoření služby WCF

1. V nabídce **soubor** přejděte na příkaz **Nový** a klikněte na **projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzel **Visual Basic** nebo **Visual C#**  a klikněte na možnost **WCF**a následně na položku **Knihovna služby WCF**. Kliknutím na tlačítko **OK** otevřete projekt.

     ![Projekt knihovny služby WCF](../data-tools/media/wcf1.PNG "wcf1")

    > [!NOTE]
    > Tím se vytvoří funkční služba, kterou lze otestovat a použít. Následující dva kroky ukazují, jak můžete změnit výchozí metodu, aby používala jiný datový typ. Ve skutečné aplikaci byste do služby přidali také vlastní funkce.

3. ![Soubor IService1](../data-tools/media/wcf2.png "wcf2")

     V **Průzkumník řešení**dvakrát klikněte na IService1. vb nebo IService1.cs a vyhledejte následující řádek:

     [!code-csharp[WCFWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1_2.cs#4)]
     [!code-vb[WCFWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1_2.vb#4)]

     Změňte typ parametru `value` na `String`:

     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

     Ve výše uvedeném kódu si poznamenejte atributy `<OperationContract()>` nebo `[OperationContract]`. Tyto atributy jsou vyžadovány pro jakoukoliv metodu zveřejněnou službou.

4. ![Soubor Service1](../data-tools/media/wcf3.png "wcf3")

     V **Průzkumník řešení**dvakrát klikněte na Service1. vb nebo Service1.cs a vyhledejte následující řádek:

     [!code-csharp[WCFWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1_2.cs#5)]
     [!code-vb[WCFWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1_2.vb#5)]

     Změňte typ parametru value na `String`:

     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]

## <a name="testing-the-service"></a>Testování služby

#### <a name="to-test-a-wcf-service"></a>Testování služby WCF

1. Stisknutím klávesy **F5** spusťte službu. Zobrazí se formulář **testovacího klienta WCF** a načte se služba.

2. Ve formuláři **testovacího klienta WCF** poklikejte na metodu **GetData ()** pod **IService1**. Zobrazí se karta **GetData** .

     ![Metoda GetData&#40; &#41;](../data-tools/media/wcf4.png "wcf4")

3. V poli **žádost** vyberte pole **hodnota** a zadejte `Hello`.

     ![Pole hodnota](../data-tools/media/wcf5.png "wcf5")

4. Klikněte na tlačítko **vyvolat** . Pokud se zobrazí dialogové okno **Upozornění zabezpečení** , klikněte na tlačítko **OK**. Výsledek se zobrazí v poli **odpověď** .

     ![Výsledek v poli Response (odpověď)](../data-tools/media/wcf6.png "wcf6")

5. V nabídce **soubor** klikněte na příkaz **ukončit** a zavřete formulář testu.

## <a name="accessing-the-service"></a>Přístup ke službě

#### <a name="to-reference-a-wcf-service"></a>Odkazování na službu WCF

1. V nabídce **soubor** přejděte na příkaz **Přidat** a potom klikněte na možnost **Nový projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzel **Visual Basic** nebo **Visual C#**  a vyberte možnost **Windows**a pak vyberte možnost **model Windows Forms aplikace**. Kliknutím na tlačítko **OK** otevřete projekt.

     ![Projekt aplikace model Windows Forms](../data-tools/media/wcf7.png "wcf7")

3. Klikněte pravým tlačítkem na **WindowsApplication1** a klikněte na **Přidat odkaz na službu**. Zobrazí se dialogové okno **Přidat odkaz na službu** .

4. V dialogovém okně **Přidat odkaz na službu** klikněte na možnost **zjistit**.

     ![Dialogové okno Přidat odkaz na službu](../data-tools/media/wcf8.png "wcf8")

     **Service1** se zobrazí v podokně **služby** .

5. Kliknutím na tlačítko **OK** přidejte odkaz na službu.

#### <a name="to-build-a-client-application"></a>Sestavení klientské aplikace

1. V **Průzkumník řešení**dvakrát klikněte na **Form1. vb** nebo **Form1.cs** a otevřete Návrhář formulářů, pokud ještě není otevřený.

2. Z **panelu nástrojů**přetáhněte ovládací prvek `TextBox`, ovládací prvek `Label` a ovládací prvek `Button` do formuláře.

     ![Přidání ovládacích prvků do formuláře](../data-tools/media/wcf9.png "wcf9")

3. Poklikejte na `Button` a přidejte následující kód do obslužné rutiny události `Click`:

     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

4. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **WindowsApplication1** a klikněte na **nastavit jako spouštěný projekt**.

5. Stisknutím klávesy **F5** spusťte projekt. Zadejte nějaký text a klikněte na tlačítko. Popisek se zobrazí "zadali jste:" a text, který jste zadali.

     ![Formulář zobrazující výsledek](../data-tools/media/wcf10.png "wcf10")

## <a name="see-also"></a>Viz také
 [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
