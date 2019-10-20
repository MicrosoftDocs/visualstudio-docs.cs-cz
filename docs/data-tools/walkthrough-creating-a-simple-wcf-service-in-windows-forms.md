---
title: 'Návod: Vytvoření jednoduché služby WCF v model Windows Forms'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7e2954d333ae3fe0dc6ff1c221d1e450eb9bf51a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639462"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Návod: Vytvoření jednoduché služby WCF v model Windows Forms

Tento návod ukazuje, jak vytvořit jednoduchou službu Windows Communication Foundation (WCF), otestovat ji a pak k ní přistoupit z aplikace model Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>Vytvoření služby

1. Otevřete Visual Studio.

::: moniker range="vs-2017"

2. V nabídce **soubor** vyberte možnost **Nový** > **projekt**.

3. V dialogovém okně **Nový projekt** rozbalte uzel **Visual Basic** nebo **Visual C#**  a vyberte možnost **WCF**a pak položku **Knihovna služby WCF**.

4. Kliknutím na tlačítko **OK** vytvořte projekt.

   ![Projekt knihovny služby WCF](../data-tools/media/wcf1.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. V okně Start vyberte možnost **vytvořit nový projekt**.

3. Do vyhledávacího pole na stránce **vytvořit nový projekt** zadejte **Knihovna služby WCF** . C# Vyberte šablonu Visual Basic pro **knihovnu služby WCF**a potom klikněte na tlačítko **Další**.

   ![Vytvoření nového projektu knihovny služby WCF v aplikaci Visual Studio 2019](media/vs-2019/create-new-wcf-service-library.png)

   > [!TIP]
   > Pokud nevidíte žádné šablony, možná budete muset nainstalovat **Windows Communication Foundation** součást sady Visual Studio. Kliknutím na **nainstalovat další nástroje a funkce** otevřete instalační program pro Visual Studio. Zvolte kartu **jednotlivé komponenty** , přejděte dolů k **aktivitám vývoje**a pak vyberte **Windows Communication Foundation**. Klikněte na **Upravit**.

4. Na stránce **Konfigurace nového projektu** klikněte na **vytvořit**.

::: moniker-end

   > [!NOTE]
   > Tím se vytvoří funkční služba, kterou lze otestovat a použít. Následující dva kroky ukazují, jak můžete změnit výchozí metodu, aby používala jiný datový typ. Ve skutečné aplikaci byste do služby přidali také vlastní funkce.

5. V **Průzkumník řešení**dvakrát klikněte na **IService1. vb** nebo **IService1.cs**.

   ![Soubor IService1](../data-tools/media/wcf2.png)

   Vyhledejte následující řádek:

   [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
   [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

   Změňte typ parametru `value` na řetězec:

   [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
   [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

   Ve výše uvedeném kódu si poznamenejte atributy `<OperationContract()>` nebo `[OperationContract]`. Tyto atributy jsou vyžadovány pro jakoukoliv metodu zveřejněnou službou.

6. V **Průzkumník řešení**dvakrát klikněte na **Service1. vb** nebo **Service1.cs**.

   ![Soubor Service1](../data-tools/media/wcf3.png)

   Vyhledejte následující řádek:

   [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
   [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

   Změňte typ parametru `value` na řetězec:

   [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
   [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Testování služby

1. Stisknutím klávesy **F5** spusťte službu. Zobrazí se formulář **testovacího klienta WCF** a služba se načte.

2. Ve formuláři **testovacího klienta WCF** poklikejte na metodu **GetData ()** pod **IService1**. Zobrazí se karta **GetData** .

     ![Metoda GetData&#40; &#41;](../data-tools/media/wcf4.png)

3. V poli **žádost** vyberte pole **hodnota** a zadejte `Hello`.

     ![Pole hodnota](../data-tools/media/wcf5.png)

4. Klikněte na tlačítko **vyvolat** . Pokud se zobrazí dialogové okno **Upozornění zabezpečení** , klikněte na tlačítko **OK**. Výsledek se zobrazí v poli **odpověď** .

     ![Výsledek v poli Response (odpověď)](../data-tools/media/wcf6.png)

5. V nabídce **soubor** klikněte na příkaz **ukončit** a zavřete formulář testu.

## <a name="access-the-service"></a>Přístup ke službě

### <a name="reference-the-wcf-service"></a>Odkaz na službu WCF

1. V nabídce **soubor** přejděte na příkaz **Přidat** a potom klikněte na možnost **Nový projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzel **Visual Basic** nebo **Visual C#**  , vyberte možnost **Windows**a potom vyberte možnost **model Windows Forms aplikace**. Kliknutím na tlačítko **OK** otevřete projekt.

     ![Projekt aplikace model Windows Forms](../data-tools/media/wcf7.png)

3. Klikněte pravým tlačítkem na **WindowsApplication1** a klikněte na **Přidat odkaz na službu**. Zobrazí se dialogové okno **Přidat odkaz na službu** .

4. V dialogovém okně **Přidat odkaz na službu** klikněte na možnost **zjistit**.

     ![Dialogové okno Přidat odkaz na službu](../data-tools/media/wcf8.png)

     **Service1** se zobrazí v podokně **služby** .

5. Kliknutím na tlačítko **OK** přidejte odkaz na službu.

### <a name="build-a-client-application"></a>Sestavení klientské aplikace

1. V **Průzkumník řešení**dvakrát klikněte na **Form1. vb** nebo **Form1.cs** a otevřete Návrhář formulářů, pokud ještě není otevřený.

2. Z **panelu nástrojů**přetáhněte ovládací prvek `TextBox`, ovládací prvek `Label` a ovládací prvek `Button` do formuláře.

     ![Přidání ovládacích prvků do formuláře](../data-tools/media/wcf9.png)

3. Poklikejte na `Button` a přidejte následující kód do obslužné rutiny události `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **WindowsApplication1** a klikněte na **nastavit jako spouštěný projekt**.

5. Stisknutím klávesy **F5** spusťte projekt. Zadejte nějaký text a klikněte na tlačítko. Popisek zobrazí "zadali jste:" a zobrazí se text, který jste zadali.

     ![Formulář zobrazující výsledek](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Viz také:

- [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)