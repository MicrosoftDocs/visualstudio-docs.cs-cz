---
title: Vytvoření zásuvné moduly zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97952f65d78f7204410d07b90e0e538fb8499116
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589120"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Postup: Vytvoření modulu plug-in zátěžového testu

Lze vytvořit modul plug-in zátěžového testu pro spuštění kódu v různých časech, zatímco zátěžový test běží. Můžete vytvořit modul plug-in pro rozšíření nebo úpravu integrované funkce zátěžového testu. Lze například naprogramovat modul plug-in zátěžového testu pro nastavení nebo úpravu průběhu zátěžového testu, zatímco zátěžový test běží. Za tímto účelem je nutné vytvořit třídu, která dědí z rozhraní <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. Tato třída musí implementovat metodu <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> tohoto rozhraní. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!TIP]
> Můžete také vytvořit moduly plug-in pro testy výkonu webu. Další informace naleznete v [tématu Postup: Vytvoření modulu plug-in test výkonu webu](../test/how-to-create-a-web-performance-test-plug-in.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>Vytvoření zásuvné modulu zátěžového testu v c #
<!-- markdownlint-enable MD003 MD020 -->

1. Otevřete webový výkon a zatížení testovací projekt, který obsahuje test výkonu webu.

2. Přidejte zátěžový test do testovacího projektu a nakonfigurujte jej tak, aby spouštěl test výkonu webu.

     Další informace naleznete [v tématu Úvodní příručka: Vytvoření projektu zátěžového testu](../test/quickstart-create-a-load-test-project.md).

3. Přidejte do řešení nový projekt **knihovny tříd.** (V **Průzkumníku řešení**klikněte pravým tlačítkem myši na řešení a vyberte **Přidat** a pak zvolte **Nový projekt**.)

4. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na složku **Reference** v nové knihovně tříd a vyberte příkaz **Přidat odkaz**.

   Zobrazí se dialogové okno **Přidat odkaz.**

5. Zvolte kartu **.NET,** posuňte se dolů a pak vyberte **Microsoft.VisualStudio.QualityTools.LoadTestFramework**.

6. Vyberte **OK**.

   Odkaz na **Microsoft.VisualStudio.QualityTools.LoadTestFramework** je přidán do složky **Reference** v **Průzkumníku řešení**.

7. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na horní uzel projektu webového výkonu a zátěžového testu, který obsahuje zátěžový test, do kterého chcete přidat modul plug-in zátěžového testu, a vyberte **přidat odkaz**.

   Zobrazí se **dialogové okno Přidat odkaz**.

8. Zvolte kartu **Projekty** a vyberte Projekt knihovny tříd.

9. Vyberte **OK**.

10. V **Editoru kódu** `using` přidejte <xref:Microsoft.VisualStudio.TestTools.LoadTesting> příkaz pro obor názvů.

11. Ve třídě vytvořené v projektu knihovny tříd implementujte rozhraní <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. V následujícím oddílu s příklady naleznete ukázku implementace.

12. Poté, co jste napsali kód, vytvořte nový projekt.

13. Klikněte pravým tlačítkem myši na horní uzel zátěžového testu a pak zvolte **Přidat modul plug-in zátěžového testu**.

     Zobrazí se dialogové okno **Přidat zatěžovací test plug-in.**

14. V části **Vyberte modul plug-in**vyberte třídu zásuvných modulů zátěžového testu.

15. V **podokně Vlastnosti vybraného modulu plug-in** nastavte počáteční hodnoty pro modul plug-in, které mají být používány za běhu.

    > [!NOTE]
    > Z modulu plug-in lze vystavit libovolný počet vlastností, ale je třeba je nastavit jako veřejné a nastavitelné a musí mít základní typ, jako je například Integer, Boolean nebo String. Můžete také změnit vlastnosti modulu plug-in test výkonu webu později pomocí okna **Vlastnosti.**

16. Vyberte **OK**.

     Modul plug-in je přidán do složky **modulů plug-in zátěžového testu.**

    > [!WARNING]
    > Při spuštění testu výkonu webu nebo zátěžového testu, který používá váš modul plug-in, se může zobrazit chyba podobná následující:
    >
    > **Požadavek se \<nezdařil: Výjimka v akci> modulu plug-in: Nelze načíst soubor nebo sestavení '\<"Název modulu plug-in".dll soubor>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null nebo jednu z jeho závislostí. Systém nemůže najít zadaný soubor.**
    >
    > To je způsobeno, pokud provedete změny kódu některého z modulů plug-in a vytvoříte novou verzi dll **(Version = 0.0.0.0)**, ale modul plug-in stále odkazuje na původní verzi modulu plug-in. Chcete-li tento problém vyřešit, postupujte takto:
    >
    > 1. Ve vašem projektu výkonu webu a zátěžového testu se zobrazí upozornění v odkazech. Odeberte a znovu přidejte odkaz na datovou dll modulu plug-in.
    > 2. Odeberte modul plug-in z testu nebo příslušného umístění a přidejte jej zpět.

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

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postup: Vytvoření modulu plug-in test výkonu webu](../test/how-to-create-a-web-performance-test-plug-in.md)
