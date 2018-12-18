---
title: Vytvoření modulu Plugin pro zátěžový Test
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c106eeda8ad3fd1f9293d6f7c3c7df1a8b48767b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064715"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Postupy: vytvoření modulu Plugin pro zátěžový test

Lze vytvořit modul plug-in zátěžového testu pro spuštění kódu v různých časech, zatímco zátěžový test běží. Můžete vytvořit modul plug-in pro rozšíření nebo úpravu integrované funkce zátěžového testu. Lze například naprogramovat modul plug-in zátěžového testu pro nastavení nebo úpravu průběhu zátěžového testu, zatímco zátěžový test běží. Za tímto účelem je nutné vytvořit třídu, která dědí z rozhraní <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. Tato třída musí implementovat metodu <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> tohoto rozhraní. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!NOTE]
> Můžete také vytvořit moduly plug-in pro testy výkonnosti webu. Další informace najdete v tématu [postupy: vytvoření modulu Plugin pro test výkonnosti webu](../test/how-to-create-a-web-performance-test-plug-in.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-load-test-plug-in-by-using-visual-c"></a>Můžete vytvořit modul plug-in zátěžového testu pomocí jazyka Visual C#

1.  Otevřete webový výkon a projekt zátěžového testu, který obsahuje test výkonnosti webu.

2.  Přidejte zátěžový test do projektu testu a nakonfigurovat jej pro spuštění testu výkonnosti webu.

     Další informace najdete v tématu [rychlý start: vytvoření projektu zátěžového testu](../test/quickstart-create-a-load-test-project.md).

3.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení a vyberte **přidat** a klikněte na tlačítko **nový projekt**.

     **Přidat nový projekt** se zobrazí dialogové okno.

4.  V části **nainstalované šablony**vyberte **Visual C#**.

5.  V seznamu šablon vyberte **knihovny tříd**.

6.  V **název** textového pole zadejte název vaší třídy.

7.  Zvolte **OK**.

8.  Nový projekt knihovny tříd je přidána do **Průzkumníka řešení** a nová třída se objeví v **Editor kódu**.

9. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** složku novou knihovnu tříd a vyberte **přidat odkaz**.

10. **Přidat odkaz** se zobrazí dialogové okno.

11. Zvolte **.NET** kartu, posuňte se dolů a pak vyberte **Microsoft.VisualStudio.QualityTools.LoadTestFramework**.

12. Zvolte **OK**.

     Odkaz na **Microsoft.VisualStudio.QualityTools.LoadTestFramework** se přidá do **odkaz** složky **Průzkumníka řešení**.

13. V **Průzkumníka řešení**, klikněte pravým tlačítkem na nejvyšší uzel webového výkonu a zatížení testovacího projektu, který obsahuje zátěžový test, ke kterému chcete přidat zátěžový test modulu plug-in a vyberte **přidat odkaz**.

14. **Zobrazí se dialogové okno Přidat odkaz**.

15. Zvolte **projekty** kartě a vyberte projekt knihovny tříd.

16. Zvolte **OK**.

17. V **Editor kódu**, přidejte `using` příkaz pro <xref:Microsoft.VisualStudio.TestTools.LoadTesting> oboru názvů.

18. Ve třídě vytvořené v projektu knihovny tříd implementujte rozhraní <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. V následujícím oddílu s příklady naleznete ukázku implementace.

19. Poté, co jste napsali kód, vytvořte nový projekt.

20. Klikněte pravým tlačítkem na nejvyšší uzel zátěžového testu a pak zvolte **přidat modul Plug-in zátěžového testu**.

     **Přidat modul Plug-in zátěžového testu** se zobrazí dialogové okno.

21. V části **vyberte modul plug-in**vyberte modul plug-in třídu testu zatížení.

22. V **vlastnosti pro vybraný modul plug-in** podokno, nastavte počáteční hodnoty pro modul plug-in pro použití v době běhu.

    > [!NOTE]
    > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Můžete také změnit modul plug-in vlastností testu výkonnosti webu později pomocí **vlastnosti** okna.

23. Zvolte **OK**.

     Modul plug-in je přidán do **moduly plug-in zátěžového testu** složky.

    > [!WARNING]
    > Vám může se objevit chyba podobná následující při spuštění testu výkonnosti webu nebo zátěžového testu, který používá modul plug-in:
    >
    > **Požadavek se nezdařil.: výjimky v \<modulu plug-in > události: Nelze načíst soubor nebo sestavení "\<soubor DLL""modulu Plug-in název >, verze =\<n.n.n.n >, jazykovou verzi = neutral, PublicKeyToken = null' nebo některou z jeho závislostí. Systém nemůže najít zadaný soubor.**
    >
    > Důvodem je-li změnit kód na některý z modulů plug-in a vytvořit novou verzi knihovny DLL **(verze = 0.0.0.0)**, ale modul plug-in stále odkazuje původní verzi modulu plug-in. Chcete-li tento problém, postupujte podle těchto kroků:
    >
    > 1.  Webový výkon a projekt zátěžového testu zobrazí se v odkazech zobrazí upozornění. Odeberte a znovu přidejte odkaz na knihovnu DLL Doplňku.
    > 2.  Odeberte doplněk z vašeho testu nebo vhodného místa a znovu ho přidejte.

## <a name="example"></a>Příklad

Následující kód ukazuje modul plug-in zátěžového testu, který spouští vlastní kód poté, co dojde k události LoadTestFinished. Pokud je tento kód spuštěn na testovacím agentu na vzdáleném počítači a tento testovací agent nemá službu SMTP localhost, zátěžový test zůstane ve stavu „Probíhá“, protože se otevře okno se zprávou.

> [!NOTE]
> Následující kód vyžaduje přidání odkazu na System.Windows.Forms.


```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

Se zátěžovým testem je spojeno osm událostí, které mohou být zpracovány v modulu plug-in zátěžového testu pro spuštění vlastního kódu se zátěžovým testem. Následuje seznam událostí, které umožňují přístup do různých období běhu zátěžového testu:

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Vytvoření vlastního kódu a modulů Plugin pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postupy: vytvoření modulu Plugin pro test výkonnosti webu](../test/how-to-create-a-web-performance-test-plug-in.md)