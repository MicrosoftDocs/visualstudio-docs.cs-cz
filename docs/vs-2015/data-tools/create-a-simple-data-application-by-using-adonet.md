---
title: Vytvoření jednoduché datové aplikace pomocí ADO.NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 46
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b524c9d630f30edd226265ac150ef7ec4f6c60d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651077"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Vytvoření jednoduché datové aplikace pomocí ADO.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když vytváříte aplikaci, která pracuje s daty v databázi, provádíte základní úlohy, jako je definování připojovacích řetězců, vkládání dat a spouštění uložených procedur. Podle tohoto tématu můžete zjistit, jak pracovat s databází z jednoduchého model Windows Forms aplikace "Forms over data" pomocí vizuálů C# nebo Visual Basic a ADO.NET.  Všechny datové technologie .NET, včetně datových sad, LINQ to SQL a Entity Framework, nakonec provádějí kroky, které jsou velmi podobné těm, které jsou uvedené v tomto článku.

 Tento článek ukazuje jednoduchý způsob, jak rychle získat data z databáze. Pokud vaše aplikace potřebuje upravovat data v netriviálních způsobech a aktualizovat databázi, měli byste zvážit použití Entity Framework a použití datových vazeb k automatické synchronizaci ovládacích prvků uživatelského rozhraní se změnami v podkladových datech.

> [!IMPORTANT]
> Aby byl kód jednoduchý, nezahrnuje zpracování výjimek připravené pro produkční prostředí.

 **V tomto tématu**

- [Nastavení ukázkové databáze](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)

- [Vytvoření formulářů a přidání ovládacích prvků](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)

- [Uložení připojovacího řetězce](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)

- [Načtení připojovacího řetězce](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)

- [Zápis kódu pro formuláře](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)

- [Testování aplikace](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)

## <a name="prerequisites"></a>Požadavky
 Chcete-li vytvořit aplikaci, budete potřebovat:

- Visual Studio Community Edition.

- SQL Server Express LocalDB.

- Malá ukázková databáze, kterou vytvoříte pomocí postupu v části [Vytvoření databáze SQL pomocí skriptu](../data-tools/create-a-sql-database-by-using-a-script.md).

- Připojovací řetězec pro databázi po jejím nastavení. Tuto hodnotu můžete najít otevřením **Průzkumník objektů systému SQL Server**, otevřením místní nabídky pro databázi, výběrem **vlastností**a přechodem na vlastnost **ConnectionString** .

  Toto téma předpokládá, že jste obeznámeni se základními funkcemi integrovaného vývojového prostředí (IDE) sady Visual Studio a můžete vytvořit aplikaci model Windows Forms, přidat do tohoto projektu formuláře, umístit tlačítka a další ovládací prvky do těchto formulářů, nastavit vlastnosti těchto ovládacích prvků a kódovat jednoduché události. . Pokud s těmito úlohami nejste spokojeni, doporučujeme, abyste před zahájením tohoto tématu dokončili [Začínáme s Visual C# a Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) .

## <a name="BKMK_setupthesampledatabase"></a>Nastavení ukázkové databáze
 Ukázková databáze pro tento návod se skládá z tabulek zákazníků a objednávek. Tabulky neobsahují žádné počáteční údaje, ale data přidáte při spuštění aplikace, kterou vytvoříte. Databáze má také pět jednoduchých uložených procedur. [Vytvoření databáze SQL pomocí skriptu](../data-tools/create-a-sql-database-by-using-a-script.md) obsahuje skript Transact-SQL, který vytvoří tabulky, primární a cizí klíče, omezení a uložené procedury.

## <a name="BKMK_createtheformsandaddcontrols"></a>Vytvoření formulářů a přidání ovládacích prvků

1. Vytvořte projekt pro aplikaci model Windows Forms a pojmenujte ji SimpleDataApp.

    Visual Studio vytvoří projekt a několik souborů, včetně prázdného formuláře Windows s názvem Form1.

2. Přidejte do projektu dva formuláře Windows, aby měly tři formuláře, a pak jim přidělte tyto názvy:

   - Navigace

   - NewCustomer

   - FillOrCancel

3. U každého formuláře přidejte textová pole, tlačítka a další ovládací prvky, které se zobrazí na následujících obrázcích. Pro každý ovládací prvek nastavte vlastnosti, které tabulky popisují.

   > [!NOTE]
   > Pole skupiny a ovládací prvky Label přidávají přehlednost, ale nepoužívají se v kódu.

   **Navigační formulář**

   ![Navigační dialogové okno](../data-tools/media/simpleappnav.png "SimpleAppNav")

|Ovládací prvky pro navigační formulář|Vlastnosti|
|--------------------------------------|----------------|
|Tlačítko|Název = btnGoToAdd|
|Tlačítko|Název = btnGoToFillOrCancel|
|Tlačítko|Název = btnExit|

 **Formulář NewCustomer**

 ![Přidat nového zákazníka a umístit objednávku](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")

|Ovládací prvky pro formulář NewCustomer|Vlastnosti|
|---------------------------------------|----------------|
|TextBox|Název = txtCustomerName|
|TextBox|Název = txtCustomerID<br /><br /> ReadOnly = true|
|Tlačítko|Název = btnCreateAccount|
|NumericUpdown|Počet desetinných míst = 0<br /><br /> Maximum = 5000<br /><br /> Název = numOrderAmount|
|DateTimePicker|Formát = krátký<br /><br /> Název = dtpOrderDate|
|Tlačítko|Název = btnPlaceOrder|
|Tlačítko|Název = btnAddAnotherAccount|
|Tlačítko|Název = btnAddFinish|

 **Formulář FillOrCancel**

 ![vyplnit nebo zrušit objednávky](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")

|Ovládací prvky pro formulář FillOrCancel|Vlastnosti|
|----------------------------------------|----------------|
|TextBox|Název = txtOrderID|
|Tlačítko|Název = btnFindByOrderID|
|DateTimePicker|Formát = krátký<br /><br /> Název = dtpFillDate|
|DataGridView|Název = dgvCustomerOrders<br /><br /> ReadOnly = true<br /><br /> RowHeadersVisible = false|
|Tlačítko|Název = btnCancelOrder|
|Tlačítko|Název = btnFillOrder|
|Tlačítko|Název = btnFinishUpdates|

## <a name="BKMK_storetheconnectionstring"></a>Uložení připojovacího řetězce
 Když se aplikace pokusí otevřít připojení k databázi, aplikace musí mít přístup k připojovacímu řetězci. Chcete-li se vyhnout zadávání řetězce ručně na každém formuláři, uložte řetězec do konfiguračního souboru aplikace v projektu a vytvořte metodu, která vrátí řetězec, pokud je metoda volána z libovolného formuláře v aplikaci.

 Připojovací řetězec můžete najít v **Průzkumník objektů systému SQL Server** tak, že kliknete pravým tlačítkem na databázi, vyberete **vlastnosti**a pak najdete vlastnost ConnectionString. Pomocí kombinace kláves CTRL + A vyberte řetězec.

1. V **Průzkumník řešení**vyberte uzel **vlastnosti** v rámci projektu a pak vyberte **nastavení. nastavení**.

2. Do sloupce **název** zadejte `connString`.

3. V seznamu **typ** vyberte **(připojovací řetězec)** .

4. V seznamu **Rozsah** vyberte možnost **aplikace**.

5. Ve sloupci **hodnota** zadejte připojovací řetězec (bez žádných vnějších uvozovek) a pak změny uložte.

> [!NOTE]
> V reálné aplikaci byste měli připojovací řetězec bezpečně ukládat, jak je popsáno v části [připojovací řetězce a konfigurační soubory](https://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8).

## <a name="BKMK_retrievetheconnectionstring"></a>Načtení připojovacího řetězce

1. Na panelu nabídek vyberte **projekt**  > **Přidat odkaz**a pak přidejte odkaz na System. Configuration. dll.

2. Na panelu nabídek vyberte **projekt**  > **Přidat třídu** pro přidání souboru třídy do projektu a potom název `Utility` souboru.

     Visual Studio vytvoří soubor a zobrazí ho v **Průzkumník řešení**.

3. V souboru nástroje nahraďte zástupný kód následujícím kódem. Všimněte si očíslovaných komentářů (s předponou Util), které identifikují oddíly kódu. Tabulka, která následuje kód, volá klíčové body.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    //Util-1 More namespaces.
    using System.Configuration;

    namespace SimpleDataApp
    {
        internal class Utility
        {

            //Get the connection string from App config file.
            internal static string GetConnectionString()
            {
                //Util-2 Assume failure.
                string returnValue = null;

                //Util-3 Look for the name in the connectionStrings section.
                ConnectionStringSettings settings =
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];

                //If found, return the connection string.
                if (settings != null)
                    returnValue = settings.ConnectionString;

                return returnValue;
            }
        }
    }
    ```

    ```vb
    Imports System
    Imports System.Collections.Generic
    Imports System.Linq
    Imports System.Text
    Imports System.Threading.Tasks
    ' Util-1 More namespaces.
    Imports System.Configuration

    Namespace SimpleDataApp
        Friend Class Utility

            ' Get connection string from App config file.
            Friend Shared Function GetConnectionString() As String

                ' Util-2 Assume failure.
                Dim returnValue As String = Nothing

                ' Util-3 Look for the name in the connectionStrings section.
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")

                ' If found, return the connection string.
                If settings IsNot Nothing Then
                    returnValue = settings.ConnectionString
                End If

                Return returnValue
            End Function
        End Class
    End Namespace
    ```

    |Komentář|Popis|
    |-------------|-----------------|
    |Util – 1|Přidejte `System.Configuration` obor názvů.|
    |Util – 2|Definujte proměnnou, `returnValue` a inicializujte ji do `null` (C#) nebo `Nothing` (Visual Basic).|
    |Util – 3|I když jste zadali `connString` jako název připojovacího řetězce v okně **vlastnosti** , musíte v kódu zadat `"SimpleDataApp.Properties.Settings.connString"` (C#) nebo `"SimpleDataApp.My.MySettings.connString"` (Visual Basic).|

## <a name="BKMK_writethecodefortheforms"></a>Zápis kódu pro formuláře
 Tato část obsahuje Stručné přehledy o tom, co každý formulář dělá, a zobrazuje kód, který vytváří formuláře. Číslované komentáře identifikují oddíly kódu.

### <a name="navigation-form"></a>Navigační formulář
 Navigační formulář se otevře při spuštění aplikace. Tlačítko **Přidat účet** otevře formulář NewCustomer. Tlačítko **vyplnit nebo zrušit objednávky** otevře formulář FillOrCancel. Tlačítko **ukončit** ukončí aplikaci.

#### <a name="make-the-navigation-form-the-startup-form"></a>Nastavit navigační formulář jako úvodní formulář
 Pokud používáte C#, v **Průzkumník řešení**otevřete Program.cs a pak změňte `Application.Run` řádek na toto: `Application.Run(new Navigation());`

 Pokud používáte Visual Basic, v **Průzkumník řešení**otevřete okno **vlastnosti** , vyberte kartu **aplikace** a pak v seznamu **spouštěcí formulář** vyberte **SimpleDataApp. Navigation** .

#### <a name="create-event-handlers"></a>Vytváření obslužných rutin událostí
 Dvojím kliknutím na tři tlačítka na formuláři Vytvořte prázdné metody obslužných rutin událostí.

#### <a name="create-code-for-navigation"></a>Vytvořit kód pro navigaci
 V navigačním formuláři nahraďte existující kód následujícím kódem.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace SimpleDataApp
{
    public partial class Navigation : Form
    {
        public Navigation()
        {
            InitializeComponent();
        }

        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.
        private void btnGoToAdd_Click(object sender, EventArgs e)
        {
            Form frm = new NewCustomer();
            frm.Show();
        }

        //Open the FillorCancel form as a dialog box.
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)
        {
            Form frm = new FillOrCancel();
            frm.ShowDialog();
        }

        //Close the application, not just the Navigation form.
        private void btnExit_Click(object sender, EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms

Namespace SimpleDataApp
    Partial Public Class Navigation
        Inherits Form
        Public Sub New()
            InitializeComponent()
        End Sub

        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click
            Dim frm As Form = New NewCustomer()
            frm.Show()
        End Sub

        ' Open the FillorCancel form as a dialog box.
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click
            Dim frm As Form = New FillOrCancel()
            frm.ShowDialog()
        End Sub

        ' Close the application, not just the Navigation form.
        Private Sub btnExit_Click() Handles btnExit.Click
            Me.Close()
        End Sub
    End Class
End Namespace

```

### <a name="newcustomer-form"></a>Formulář NewCustomer
 Když zadáte název zákazníka a potom kliknete na tlačítko **vytvořit účet** , formulář NewCustomer vytvoří účet zákazníka a jako nové číslo účtu se SQL Server vrátí hodnotu identity. Pak zadáte objednávku pro nový účet zadáním částky a data objednávky a kliknutím na tlačítko **umístit objednávku** .

#### <a name="create-event-handlers"></a>Vytváření obslužných rutin událostí
 Vytvořte prázdnou obslužnou rutinu události Click pro každé tlačítko ve formuláři.

#### <a name="create-code-for-newcustomer"></a>Vytvořit kód pro NewCustomer
 Do formuláře NewCustomer přidejte následující kód. Projděte jednotlivé bloky kódu pomocí očíslovaných komentářů a tabulky za kódem.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
//NC-1 More namespaces.
using System.Data.SqlClient;
using System.Configuration;

namespace SimpleDataApp
{
    public partial class NewCustomer : Form
    {
        //NC-2 Storage for IDENTITY values returned from database.
        private int parsedCustomerID;
        private int orderID;

        //NC-3 Specify a connection string.
        string connstr = SimpleDataApp.Utility.GetConnectionString();

        public NewCustomer()
        {
            InitializeComponent();
        }

        //NC-4 Create account.
        private void btnCreateAccount_Click(object sender, EventArgs e)
        {
            //NC-5 Set up and run stored procedure only if Customer Name is present.
            if (isCustomerName())
            {

                //NC-6 Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //NC-7 Create a SqlCommand, and identify it as a stored procedure.
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;

                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;

                //NC-9 Add output parameter.
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;

                //NC-10 try-catch-finally
                try
                {
                    //NC-11 Open the connection.
                    conn.Open();

                    //NC-12 Run the stored procedure.
                    cmdNewCustomer.ExecuteNonQuery();

                    //NC-13 Customer ID is an IDENTITY value from the database.
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);

                }
                catch
                {
                    //NC-14 A simple catch.

                    MessageBox.Show("Customer ID was not returned. Account could not be created.");
                }
                finally
                {
                    //NC-15 Close the connection.
                    conn.Close();
                }
            }
        }

        //NC-16 Verify that Customer Name is present.
        private bool isCustomerName()
        {
            if (txtCustomerName.Text == "")
            {
                MessageBox.Show("Please enter a name.");
                return false;
            }
            else
            {
                return true;
            }
        }

        //NC-17 Place order.
        private void btnPlaceOrder_Click(object sender, EventArgs e)
        {
            //NC-18 Set up and run stored procedure only if required input is present.
            if (isPlaceOrderReady())
            {
                // Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //NC-19 Create SqlCommand and identify it as a stored procedure.
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);
                cmdNewOrder.CommandType = CommandType.StoredProcedure;

                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;

                //NC-21 @OrderDate.
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;

                //NC-22 @Amount.
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;

                //NC-23 @Status. For a new order, the status is always O (open).
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));
                cmdNewOrder.Parameters["@Status"].Value = "O";

                //NC-24 Add return value for stored procedure, which is orderID.
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;

                //try-catch-finally
                try
                {
                    //Open connection.
                    conn.Open();

                    //Run the stored procedure.
                    cmdNewOrder.ExecuteNonQuery();

                    //NC-25 Display the order number.
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("Order could not be placed.");
                }
                finally
                {
                    //Close connection.
                    conn.Close();
                }
            }
        }

        //NC-26 Verify that order data is ready.
        private bool isPlaceOrderReady()
        {
            // Verify that CustomerID is present.
            if (txtCustomerID.Text == "")
            {
                MessageBox.Show("Please create customer account before placing order.");
                return false;
            }

            // Verify that Amount isn't 0.
            else if ((numOrderAmount.Value < 1))
            {
                MessageBox.Show("Please specify an order amount.");
                return false;
            }
            else
            {
                // Order can be submitted.
                return true;
            }
        }

        //NC-27 Reset the form for another new account.
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)
        {
            this.ClearForm();
        }

        //NC-28 Clear values from controls.
        private void ClearForm()
        {
            txtCustomerName.Clear();
            txtCustomerID.Clear();
            dtpOrderDate.Value = DateTime.Now;
            numOrderAmount.Value = 0;
            this.parsedCustomerID = 0;
        }

        //NC-29 Close the form.
        private void btnAddFinish_Click(object sender, EventArgs e)
        {
            this.Close();
        }

    }
}

```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms
' NC-1 More namespaces.
Imports System.Data.SqlClient
Imports System.Configuration

Namespace SimpleDataApp
    Partial Public Class NewCustomer
        Inherits Form

        ' NC-2 Storage for IDENTITY values returned from database.
        Private parsedCustomerID As Integer
        Private orderID As Integer

        ' NC-3 Specify a connection string.
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()

        Public Sub New()
            InitializeComponent()
        End Sub

        ' NC-4 Create account.
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click

            ' NC-5 Set up and run stored procedure only if Customer Name is present.
            If isCustomerName() Then

                ' NC-6 Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)
                cmdNewCustomer.CommandType = CommandType.StoredProcedure

                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text

                ' NC-9 Add output parameter.
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output

                ' NC-10 try-catch-finally
                Try
                    ' NC-11 Open the connection.
                    conn.Open()

                    ' NC-12 Run the stored procedure.
                    cmdNewCustomer.ExecuteNonQuery()

                    ' NC-13 Customer ID is an IDENTITY value from the database.
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)

                Catch
                    ' NC-14 A simple catch.
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")
                Finally
                    ' NC-15 Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' NC-16 Verify that Customer Name is present.
        Private Function isCustomerName() As Boolean
            If txtCustomerName.Text = "" Then
                MessageBox.Show("Please enter a name.")
                Return False
            Else
                Return True
            End If
        End Function

        ' NC-17 Place order.
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click

            ' NC-18 Set up and run stored procedure only if necessary input is present.
            If isPlaceOrderReady() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' NC-19 Create SqlCommand and identify it as a stored procedure.
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)
                cmdNewOrder.CommandType = CommandType.StoredProcedure

                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID

                ' NC-21 @OrderDate.
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value

                ' NC-22 @Amount.
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value

                ' NC-23 @Status. For a new order, the status is always O (open).
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))
                cmdNewOrder.Parameters("@Status").Value = "O"

                ' NC-24 Add return value for stored procedure, which is orderID.
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue

                ' try-catch-finally
                Try
                    ' Open connection.
                    conn.Open()

                    ' Run the stored procedure.
                    cmdNewOrder.ExecuteNonQuery()

                    ' NC-25 Display the order number.
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")

                Catch
                    ' A simple catch.
                    MessageBox.Show("Order could  not be placed.")

                Finally
                    ' Close connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' NC-26 Verify that order data is ready.
        Private Function isPlaceOrderReady() As Boolean

            ' Verify that CustomerID is present.
            If txtCustomerID.Text = "" Then
                MessageBox.Show("Please create customer account before placing order.")
                Return False

                ' Verify that Amount isn't 0.
            ElseIf (numOrderAmount.Value < 1) Then

                MessageBox.Show("Please specify an order amount.")
                Return False
            Else
                ' Order can be submitted.
                Return True
            End If
        End Function

        ' NC-27 Reset the form for another new account.
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click
            Me.ClearForm()
        End Sub

        ' NC-28 Clear values from controls.
        Private Sub ClearForm()
            txtCustomerName.Clear()
            txtCustomerID.Clear()
            dtpOrderDate.Value = DateTime.Now
            numOrderAmount.Value = 0
            Me.parsedCustomerID = 0
        End Sub

        ' NC-29 Close the form.
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click
            Me.Close()
        End Sub

    End Class
End Namespace
```

|Komentář|Popis|
|-------------|-----------------|
|NC-1|Do seznamu oborů názvů přidejte `System.Data.SqlClient` a `System.Configuration`.|
|NC – 2|Deklarujte proměnné `parsedCustomerID` a `orderID`, které použijete později.|
|NC – 3|Zavolejte metodu `GetConnectionString` pro získání připojovacího řetězce z konfiguračního souboru aplikace a uložte hodnotu do proměnné řetězce `connstr`.|
|NC-4|Přidejte kód do obslužné rutiny události Click pro tlačítko `btnCreateAccount`.|
|NC-5|Zabalte volání `isCustomerName` kolem kódu události Click, aby `uspNewCustomer` běžet pouze v případě, že je k dispozici název zákazníka.|
|NC – 6|Vytvořte objekt `SqlConnection` (`conn`) a předejte do `connstr` připojovací řetězec.|
|NC – 7|Vytvořte objekt `SqlCommand` `cmdNewCustomer`.<br /><br /> -Zadejte `Sales.uspNewCustomer` jako uloženou proceduru, která se má spustit.<br />– Pomocí vlastnosti `CommandType` určete, že příkaz představuje uloženou proceduru.|
|NC – 8|Do uložené procedury přidejte vstupní parametr `@CustomerName`.<br /><br /> – Přidejte parametr do kolekce `Parameters`.<br />-Použijte výčet `SqlDbType` k určení typu parametru jako nvarchar (40).<br />-Zadejte `txtCustomerName.Text` jako zdroj.|
|NC – 9|Přidejte výstupní parametr z uložené procedury.<br /><br /> – Přidejte parametr do kolekce `Parameters`.<br />– Pomocí `ParameterDirection.Output` Identifikujte parametr jako výstup.|
|NC-10|Přidejte blok try-catch-finally k otevření připojení, spusťte uloženou proceduru, zpracujte výjimky a pak připojení zavřete.|
|NC-11|Otevřete připojení (`conn`), které jste vytvořili v NC-6.|
|NC – 12|Pomocí metody `ExecuteNonQuery` `cmdNewCustomer` spusťte uloženou proceduru `Sales.uspNewCustomer`. Tato uložená procedura spustí příkaz `INSERT`, nikoli dotaz.|
|NC – 13|Hodnota `@CustomerID` se vrátí jako hodnota IDENTITY z databáze. Vzhledem k tomu, že se jedná o celé číslo, budete ji muset převést na řetězec, aby se zobrazila v textovém poli **ID zákazníka** .<br /><br /> – Deklarovali jste `parsedCustomerID` v NC-2.<br />– Uložte hodnotu `@CustomerID` v `parsedCustomerID` pro pozdější použití.<br />– Převeďte vrácené ID zákazníka na řetězec a vložte ho do `txtCustomerID.Text`.|
|NC – 14|Pro tuto ukázku přidejte jednoduchou klauzuli catch (ne produkční).|
|NC – 15|Připojení vždy uzavřete po jeho dokončení pomocí, aby bylo možné ho uvolnit do fondu připojení. Informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](https://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|
|NC – 16|Definujte metodu pro ověření, že je k dispozici název zákazníka.<br /><br /> – Pokud je textové pole prázdné, zobrazí zprávu a vrátí `false`, protože k vytvoření účtu se vyžaduje název.<br />– Pokud textové pole není prázdné, vrátí `true`.|
|NC – 17|Přidejte kód do obslužné rutiny události Click pro tlačítko `btnPlaceOrder`.|
|NC – 18|Zabalte volání `isPlaceOrderReady` okolo kódu události `btnPlaceOrder_Click`, aby `uspPlaceNewOrder` neběžely, pokud není přítomen požadovaný vstup.|
|NC-19 až NC-25|Tyto části kódu připomínají kód, který jste přidali pro obslužnou rutinu události `btnCreateAccount_Click`.<br /><br /> -NC-19. Vytvořte objekt `SqlCommand`, `cmdNewOrder` a jako uloženou proceduru zadejte `Sales.uspPlaceOrder`.<br />-NC-20 až NC-23 jsou vstupní parametry pro uloženou proceduru.<br />-NC-24. `@RC` bude obsahovat návratovou hodnotu, která je vygenerovaným ID objednávky z databáze. Směr tohoto parametru je určen jako `ReturnValue`.<br />-NC-25. Uloží hodnotu ID objednávky v proměnné `orderID`, kterou jste deklarovali v NC-2, a zobrazte hodnotu v okně se zprávou.|
|NC – 26|Definujte metodu pro ověření, že ID zákazníka existuje a že byla zadána částka v `numOrderAmount`.|
|NC – 27|Volejte metodu `ClearForm` v obslužné rutině události `btnAddAnotherAccount` Click.|
|NC – 28|Pokud chcete přidat dalšího zákazníka, vytvořte metodu `ClearForm` pro vymazání hodnot z formuláře.|
|NC29|Zavřete formulář NewCustomer a vraťte se fokus na navigační formulář.|

### <a name="fillorcancel-form"></a>Formulář FillOrCancel
 Formulář FillorCancel spustí dotaz, který vrátí objednávku, když zadáte ID objednávky a kliknete na tlačítko **najít objednávku** . Vrácený řádek se zobrazí v mřížce dat, která je jen pro čtení. Pokud vyberete tlačítko pro **zrušení objednávky** , můžete objednávku označit jako zrušenou (X), nebo objednávku označit jako vyplněnou (F), pokud vyberete tlačítko **pořadí výplně** . Pokud znovu vyberete tlačítko **najít objednávku** , zobrazí se aktualizovaný řádek.

#### <a name="create-event-handlers"></a>Vytváření obslužných rutin událostí
 Vytvořte prázdné obslužné rutiny události Click pro čtyři tlačítka na formuláři.

#### <a name="create-code-for-fillorcancel"></a>Vytvořit kód pro FillOrCancel
 Do formuláře FillOrCancel přidejte následující kód. Projděte bloky kódu pomocí očíslovaných komentářů a tabulky, které následují kód.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
//FC-1 More namespaces.
using System.Text.RegularExpressions;
using System.Data.SqlClient;
using System.Configuration;

namespace SimpleDataApp
{
    public partial class FillOrCancel : Form
    {
        //FC-2 Storage for OrderID.
        private int parsedOrderID;

        //FC-3 Specify a connection string.
        string connstr = SimpleDataApp.Utility.GetConnectionString();

        public FillOrCancel()
        {
            InitializeComponent();
        }

        //FC-4 Find an order.
        private void btnFindByOrderID_Click(object sender, EventArgs e)
        {
            //FC-5 Prepare the connection and the command.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //Define a query string that has a parameter for orderID.
                string sql = "select * from Sales.Orders where orderID = @orderID";

                //Create a SqlCommand object.
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);

                //Define the @orderID parameter and its value.
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;

                //try-catch-finally
                try
                {
                    //FC-6 Run the command and display the results.
                    //Open the connection.
                    conn.Open();

                    //Run the command by using SqlDataReader.
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();

                    //Create a data table to hold the retrieved data.
                    DataTable dataTable = new DataTable();

                    //Load the data from SqlDataReader into the data table.
                    dataTable.Load(rdr);

                    //Display the data from the data table in the data grid view.
                    this.dgvCustomerOrders.DataSource = dataTable;

                    //Close the SqlDataReader.
                    rdr.Close();
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("The requested order could not be loaded into the form.");
                }
                finally
                {
                    //Close the connection.
                    conn.Close();
                }
            }
        }

        //FC-7 Cancel an order.
        private void btnCancelOrder_Click(object sender, EventArgs e)
        {
            //Set up and run stored procedure only if OrderID is ready.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                // Create command and identify it as a stored procedure.
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;

                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;

                // try-catch-finally
                try
                {
                    // Open the connection.
                    conn.Open();

                    // Run the cmdCancelOrder command.
                    cmdCancelOrder.ExecuteNonQuery();
                }
                // A simple catch.
                catch
                {
                    MessageBox.Show("The cancel operation was not completed.");
                }
                finally
                {
                    //Close connection.
                    conn.Close();
                }
            }
        }

        //FC-8 Fill an order.
        private void btnFillOrder_Click(object sender, EventArgs e)
        {
            //Set up and run stored procedure only if OrderID is ready.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //Create command and identify it as a stored procedure.
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);
                cmdFillOrder.CommandType = CommandType.StoredProcedure;

                // Add input parameter from the stored procedure.
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;

                //Add the second input parameter.
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;

                //try-catch-finally
                try
                {
                    //Open the connection.
                    conn.Open();

                    //Run the cmdFillOrder command.
                    cmdFillOrder.ExecuteNonQuery();
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("The fill operation was not completed.");
                }
                finally
                {
                    //Close the connection.
                    conn.Close();
                }
            }
        }

        //FC-9 Verify that OrderID is ready.
        private bool isOrderID()
        {

            //Check for input in the Order ID text box.
            if (txtOrderID.Text == "")
            {
                MessageBox.Show("Please specify the Order ID.");
                return false;
            }

            // Check for characters other than integers.
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))
            {
               //Show message and clear input.
                MessageBox.Show("Please specify integers only.");
                txtOrderID.Clear();
                return false;
            }
            else
            {
                //Convert the text in the text box to an integer to send to the database.
                parsedOrderID = Int32.Parse(txtOrderID.Text);
                return true;
            }
        }

        //Close the form.
        private void btnFinishUpdates_Click(object sender, EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms
' FC-1 More namespaces.
Imports System.Text.RegularExpressions
Imports System.Data.SqlClient
Imports System.Configuration

Namespace SimpleDataApp
    Partial Public Class FillOrCancel
        Inherits Form
        ' FC-2 Storage for OrderID.
        Private parsedOrderID As Integer

        ' FC-3 Specify a connection string.
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()

        Public Sub New()
            InitializeComponent()
        End Sub

        ' FC-4 Find an order.
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click

            ' FC-5 Prepare the connection and the command.

            If isOrderID() Then
                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Define the query string that has a parameter for orderID.
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"

                ' Create a SqlCommand object.
                Dim cmdOrderID As New SqlCommand(sql, conn)

                ' Define the @orderID parameter and its value.
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID

                ' try-catch-finally
                Try
                    ' FC-6 Run the command and display the results.
                    ' Open connection.
                    conn.Open()

                    ' Run the command by using SqlDataReader.
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()

                    ' Create a data table to hold the retrieved data.
                    Dim dataTable As New DataTable()

                    ' Load the data from SqlDataReader into the data table.
                    dataTable.Load(rdr)

                    ' Display the data from the data table in the data grid view.
                    Me.dgvCustomerOrders.DataSource = dataTable

                    ' Close the SqlDataReader.
                    rdr.Close()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The requested order could not be loaded into the form.")
                Finally
                    ' Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-7 Cancel an order.
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click

            ' Set up and run stored procedure only if OrderID is ready.
            If isOrderID() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Create the command and identify it as a stored procedure.
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)
                cmdCancelOrder.CommandType = CommandType.StoredProcedure

                ' Add input parameter from the stored procedure.
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID

                ' try-catch-finally
                Try
                    ' Open the connection.
                    conn.Open()

                    ' Run the cmdCancelOrder command.
                    cmdCancelOrder.ExecuteNonQuery()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The cancel operation was not completed.")
                Finally
                    ' Close connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-8 Fill an order.
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click

            ' Set up and run stored procedure only if OrderID is ready.
            If isOrderID() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Create command and identify it as a stored procedure.
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)
                cmdFillOrder.CommandType = CommandType.StoredProcedure

                ' Add input parameter from the stored procedure.
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID

                ' Add second input parameter.
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value

                ' try-catch-finally
                Try
                    ' Open the connection.
                    conn.Open()

                    ' Run the cmdFillOrder command.
                    cmdFillOrder.ExecuteNonQuery()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The fill operation was not completed.")
                Finally
                    ' Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-9 Verify that OrderID is ready.
        Private Function isOrderID() As Boolean

            ' Check for input in the Order ID text box.
            If txtOrderID.Text = "" Then
                MessageBox.Show("Please specify the Order ID.")
                Return False

                ' Check for characters other than integers.
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then

                ' Show message and clear input.
                MessageBox.Show("Please specify integers only.")
                txtOrderID.Clear()
                Return False

            Else
                ' Convert the text in the text box to an integer to send to the database.
                parsedOrderID = Int32.Parse(txtOrderID.Text)
                Return True

            End If
        End Function

        ' Close the form.
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click
            Me.Close()
        End Sub
    End Class
End Namespace
```

|Komentář|Popis|
|-------------|-----------------|
|FC-1|Do seznamu oborů názvů přidejte `System.Data.SqlClient`, `System.Configuration` a `System.Text.RegularExpressions`.|
|FC – 2|Deklarujte `parsedOrderID` proměnnou.|
|FC-3|Zavolejte metodu `GetConnectionString` pro získání připojovacího řetězce z konfiguračního souboru aplikace a uložte hodnotu do proměnné řetězce `connstr`.|
|FC-4|Přidejte kód do obslužné rutiny události Click pro `btnFindOrderByID`.|
|FC-5|Tyto úlohy jsou požadovány, než se pokusíte spustit příkaz SQL nebo uloženou proceduru.<br /><br /> -Vytvořit objekt `SqlConnection`.<br />-Definujte příkaz SQL nebo zadejte název uložené procedury. (V tomto případě spustíte příkaz `SELECT`.)<br />-Vytvořit objekt `SqlCommand`.<br />-Definujte parametry pro příkaz SQL nebo uloženou proceduru.|
|FC-6|Tento kód používá `SqlDataReader` a `DataTable` k načtení a zobrazení výsledku dotazu.<br /><br /> -Otevřete připojení.<br />-Vytvořte objekt `SqlDataReader` `rdr` spuštěním metody `ExecuteReader` pro `cmdOrderID`.<br />– Vytvořte objekt `DataTable` pro uložení načtených dat.<br />– Načtěte data z objektu `SqlDataReader` do objektu `DataTable`.<br />– Zobrazí data v zobrazení datové mřížky zadáním `DataTable` jako `DataSource` pro zobrazení datové mřížky.<br />-Zavřít `SqlDataReader`.|
|FC-7|Přidejte kód do obslužné rutiny události Click pro `btnCancelOrder`. Tento kód spustí uloženou proceduru `Sales.uspCancelOrder`.|
|FC-8|Přidejte kód do obslužné rutiny události Click pro `btnFillOrder`. Tento kód spustí uloženou proceduru `Sales.uspFillOrder`.|
|FC – 9|Vytvořte metodu pro ověření, zda je `OrderID` připravena k odeslání jako parametru do objektu `SqlCommand`.<br /><br /> – Ujistěte se, že bylo zadáno ID do `txtOrderID`.<br />-Použijte `Regex.IsMatch` k definování jednoduché kontroly znaků, které nejsou celé číslo.<br />– Deklarujete `parsedOrderID` proměnnou na FC-2.<br />– Pokud je vstup platný, převeďte text na celé číslo a uložte hodnotu do proměnné `parsedOrderID`.<br />-Zabalte `isOrderID` metodu kolem `btnFindByOrderID`, `btnCancelOrder` a obslužné rutiny událostí kliknutí na `btnFillOrder`.|

## <a name="BKMK_testyourapplication"></a>Testování aplikace
 Vyberte klávesu F5 pro sestavení a otestování aplikace po kódu každé obslužné rutiny události Click a poté po dokončení kódování.
