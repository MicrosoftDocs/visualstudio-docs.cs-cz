---
title: Vytvoření modulu plug-in zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2eea116eb18e192720410b71136de9d823ed0fe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653669"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Postupy: Vytvoření modulu plug-in zátěžového testu

Lze vytvořit modul plug-in zátěžového testu pro spuštění kódu v různých časech, zatímco zátěžový test běží. Můžete vytvořit modul plug-in pro rozšíření nebo úpravu integrované funkce zátěžového testu. Lze například naprogramovat modul plug-in zátěžového testu pro nastavení nebo úpravu průběhu zátěžového testu, zatímco zátěžový test běží. Za tímto účelem je nutné vytvořit třídu, která dědí z rozhraní <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. Tato třída musí implementovat metodu <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> tohoto rozhraní. Další informace najdete v tématu <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!TIP]
> Můžete také vytvořit moduly plug-in pro testy výkonnosti webu. Další informace najdete v tématu [Postupy: Vytvoření modulu plug-in pro test výkonnosti webu](../test/how-to-create-a-web-performance-test-plug-in.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>Vytvoření modulu plug-in zátěžového testu v nástrojiC#
<!-- markdownlint-enable MD003 MD020 -->

1. Otevřete projekt webového výkonu a zátěžového testu, který obsahuje test výkonnosti webu.

2. Přidejte zátěžový test do projektu testu a nakonfigurujte jej tak, aby běžel test výkonnosti webu.

     Další informace naleznete v tématu [rychlý Start: vytvoření projektu zátěžového testu](../test/quickstart-create-a-load-test-project.md).

3. Přidejte do řešení nový projekt **knihovny tříd** . (V **Průzkumník řešení**klikněte pravým tlačítkem na řešení a vyberte **Přidat** a pak zvolte **Nový projekt**.)

4. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **odkazy** v nové knihovně tříd a vyberte možnost **Přidat odkaz**.

   Zobrazí se dialogové okno **Přidat odkaz** .

5. Zvolte kartu **.NET** , posuňte se dolů a pak vyberte **Microsoft. VisualStudio. QualityTools. LoadTestFramework**.

6. Klikněte na **tlačítko OK**.

   Odkaz na **Microsoft. VisualStudio. QualityTools. LoadTestFramework** se přidá do **referenční** složky v **Průzkumník řešení**.

7. V **Průzkumník řešení**klikněte pravým tlačítkem myši na nejvyšší uzel projektu testování výkonu webu a zátěžového testu, který obsahuje zátěžový test, do kterého chcete přidat modul plug-in zátěžového testu, a vyberte možnost **Přidat odkaz**.

   **Zobrazí se dialogové okno Přidat odkaz**.

8. Zvolte kartu **projekty** a vyberte projekt knihovny tříd.

9. Klikněte na **tlačítko OK**.

10. V **editoru kódu**přidejte příkaz `using` pro obor názvů <xref:Microsoft.VisualStudio.TestTools.LoadTesting>.

11. Ve třídě vytvořené v projektu knihovny tříd implementujte rozhraní <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. V následujícím oddílu s příklady naleznete ukázku implementace.

12. Poté, co jste napsali kód, vytvořte nový projekt.

13. Klikněte pravým tlačítkem myši na nejvyšší uzel zátěžového testu a pak zvolte **Přidat modul plug-in zátěžového testu**.

     Zobrazí se dialogové okno **Přidat modul plug-in zátěžového testu** .

14. V části **Vybrat modul plug-in**vyberte svoji třídu modulu plug-in zátěžového testu.

15. V podokně **vlastnosti pro vybraný modul plug-in** nastavte počáteční hodnoty pro modul plug-in, které se použijí v době běhu.

    > [!NOTE]
    > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Vlastnosti modulu plug-in testu výkonnosti webu lze také změnit později pomocí okna **vlastnosti** .

16. Klikněte na **tlačítko OK**.

     Modul plug-in se přidá do složky **moduly plug-in zátěžového testu** .

    > [!WARNING]
    > Při spuštění testu výkonnosti webu nebo zátěžového testu, který používá modul plug-in, se může zobrazit chybová zpráva podobná následující:
    >
    > **Požadavek se nezdařil: výjimka v \<plug > událost: Nepodařilo se načíst soubor nebo sestavení ' \< '. soubor dll >, Version = \<n. n. n. n >, Culture = neutral, PublicKeyToken = null nebo jedna z jeho závislostí. Systém nemůže najít zadaný soubor.**
    >
    > To je způsobeno tím, že provedete změny kódu v některém z modulů plug-in a vytvoříte novou verzi knihovny DLL **(verze = 0.0.0.0)** , ale modul plug-in stále odkazuje na původní verzi modulu plug-in. Chcete-li tento problém vyřešit, postupujte podle následujících kroků:
    >
    > 1. V projektu webového výkonu a zátěžového testu se zobrazí upozornění v odkazech. Odeberte a znovu přidejte odkaz na knihovnu DLL modulu plug-in.
    > 2. Odeberte modul plug-in z testu nebo příslušné umístění a pak ho přidejte zpátky.

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

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Vytvoření vlastního kódu a modulů plug-in pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postupy: Vytvoření modulu plug-in testu výkonnosti webu](../test/how-to-create-a-web-performance-test-plug-in.md)