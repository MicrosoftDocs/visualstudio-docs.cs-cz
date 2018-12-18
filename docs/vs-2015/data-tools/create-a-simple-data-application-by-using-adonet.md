---
title: Vytvoření jednoduché datové aplikace pomocí ADO.NET | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 46
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4754cad05858ed48fd421301b4b0f1d2c569a926
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824279"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Vytvoření jednoduché datové aplikace pomocí ADO.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Když vytvoříte aplikaci, která zpracovává data v databázi, provedete základní úlohy takové definování připojovacích řetězců, vkládání dat a spouštění uložených procedur. Podle tohoto tématu můžete zjistit, jak pracovat s databází z jednoduchého "formy nad daty" aplikace Windows Forms pomocí Visual C# nebo Visual Basic a ADO.NET.  Všechna data technologie .NET, včetně datových sad, LINQ to SQL a Entity Framework – nakonec proveďte kroky, které jsou velmi podobné těm, které jsou uvedené v tomto článku.  
  
 Tento článek ukazuje jednoduchý způsob, jak získat data z databáze způsobem, velmi rychle. Pokud vaše aplikace potřebuje upravovat data nejsou v netriviálních způsoby a aktualizaci databáze, měli byste zvážit používající nástroj Entity Framework a použití datových vazeb se automaticky synchronizovat ovládacích prvků uživatelského rozhraní na změny v podkladových datech.  
  
> [!IMPORTANT]
>  Chcete-li být kód jednoduchý, neměl by zahrnovat zpracování výjimek připravené pro produkční prostředí.  
  
 **V tomto tématu**  
  
-   [Nastavení ukázkové databáze](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
-   [Vytvoření formulářů a přidání ovládacích prvků](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
-   [Store připojovací řetězec](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
-   [Načtení připojovacího řetězce](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
-   [Napište kód pro formuláře](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
-   [Testování aplikace](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li vytvořit aplikaci, budete potřebovat:  
  
- Visual Studio Community Edition.  
  
- SQL Server Express LocalDB.  
  
- Malá ukázková databáze, kterou vytvoříte podle postupu v [vytvoření databáze SQL pomocí skriptu](../data-tools/create-a-sql-database-by-using-a-script.md).  
  
- Připojovací řetězec pro databázi, jakmile ho nastavíte. Tuto hodnotu lze najít otevřením **Průzkumník objektů systému SQL Server**, otevřete místní nabídku pro databázi, že vyberete **vlastnosti**a přechodem na **ConnectionString** vlastnost.  
  
  Toto téma předpokládá, že ovládáte základní funkce integrovaného vývojového prostředí sady Visual Studio a můžete vytvořit aplikaci Windows Forms, přidat formuláře do projektu, Vložit tlačítka a další ovládací prvky na tyto formuláře, nastavit vlastnosti těchto ovládacích prvků a kódovat jednoduché události . Pokud si nejste seznámení s těmito úkoly, doporučujeme provést [Začínáme s Visual C# a Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) před započetím tohoto tématu.  
  
##  <a name="BKMK_setupthesampledatabase"></a> Nastavení ukázkové databáze  
 Vzorové databáze pro Tento názorný postup se skládá z tabulek Customer a Orders. Tabulky zpočátku neobsahují žádná data, ale přidáte data při spuštění aplikace, kterou vytvoříte. Databáze má také pět jednoduchých uložených procedur. [Vytvoření databáze SQL pomocí skriptu](../data-tools/create-a-sql-database-by-using-a-script.md) obsahuje skript Transact-SQL, který vytvoří tabulky, primární a cizí klíče, omezení a uložené procedury.  
  
##  <a name="BKMK_createtheformsandaddcontrols"></a> Vytvoření formulářů a přidání ovládacích prvků  
  
1. Vytvoření projektu aplikace Windows Forms a pojmenujte ho SimpleDataApp.  
  
    Visual Studio vytvoří projekt a několik souborů, včetně prázdný formulář Windows s názvem Form1.  
  
2. Přidejte do projektu dva formuláře Windows, tak, aby měl tři formuláře a dejte jim následující názvy:  
  
   -   Navigace  
  
   -   NewCustomer  
  
   -   FillOrCancel  
  
3. U každého formuláře přidejte textová pole, tlačítka a další ovládací prvky, které se zobrazují na následujících obrázcích. Pro každý ovládací prvek nastavte vlastnosti, které jsou popsány v tabulce.  
  
   > [!NOTE]
   >  Skupinový rámeček a ovládací prvky popisku přehlednosti, ale nepoužívají se v kódu.  
  
   **Navigační formulář**  
  
   ![Dialogové okno navigační](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|Ovládací prvky formuláře Navigation|Vlastnosti|  
|--------------------------------------|----------------|  
|Tlačítko|Název = btnGoToAdd|  
|Tlačítko|Název = btnGoToFillOrCancel|  
|Tlačítko|Název = btnExit|  
  
 **Formulář NewCustomer**  
  
 ![Přidání nového odběratele a objednávky](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
|Ovládací prvky formuláře NewCustomer|Vlastnosti|  
|---------------------------------------|----------------|  
|TextBox|Název = txtCustomerName|  
|TextBox|Název = txtCustomerID<br /><br /> Jen pro čtení = True|  
|Tlačítko|Název = btnCreateAccount|  
|NumericUpdown|Počet desetinných míst = 0<br /><br /> Maximální = 5000<br /><br /> Název = numOrderAmount|  
|Ovládacího prvku DateTimePicker|Formát = krátké<br /><br /> Název = dtpOrderDate|  
|Tlačítko|Název = btnPlaceOrder|  
|Tlačítko|Název = btnAddAnotherAccount|  
|Tlačítko|Název = btnAddFinish|  
  
 **Formulář FillOrCancel**  
  
 ![vyplnit nebo zrušit objednávky](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|Ovládací prvky formuláře FillOrCancel|Vlastnosti|  
|----------------------------------------|----------------|  
|TextBox|Název = txtOrderID|  
|Tlačítko|Název = btnFindByOrderID|  
|Ovládacího prvku DateTimePicker|Formát = krátké<br /><br /> Název = dtpFillDate|  
|Ovládací prvek DataGridView|Název = dgvCustomerOrders<br /><br /> Jen pro čtení = True<br /><br /> RowHeadersVisible = False|  
|Tlačítko|Název = btnCancelOrder|  
|Tlačítko|Název = btnFillOrder|  
|Tlačítko|Název = btnFinishUpdates|  
  
##  <a name="BKMK_storetheconnectionstring"></a> Store připojovací řetězec  
 Když vaše aplikace se pokusí otevřít připojení k databázi, musí mít vaše aplikace přístup k připojovací řetězec. Pokud chcete vyhnout ručním zadáním řetězce na každém formuláři, uložte řetězec v konfiguračním souboru aplikace ve vašem projektu a vytvořte metodu, která vrátí řetězec, když je volána metoda z libovolného formuláře v aplikaci.  
  
 Připojovací řetězec můžete najít **Průzkumník objektů systému SQL Server** tím pravým tlačítkem myši databázi, vyberte **vlastnosti**a vyhledáním vlastnost připojovací řetězec. Pomocí kombinace kláves Ctrl + A vyberte řetězec.  
  
1.  V **Průzkumníka řešení**, vyberte **vlastnosti** uzlu projektu a pak vyberte **Settings.settings**.  
  
2.  V **název** sloupce, zadejte `connString`.  
  
3.  V **typ** seznamu vyberte **(připojovací řetězec)**.  
  
4.  V **oboru** seznamu vyberte **aplikace**.  
  
5.  V **hodnotu** sloupce, zadejte svůj připojovací řetězec (bez jakékoli mimo uvozovky) a pak uložte provedené změny.  
  
> [!NOTE]
>  V reálné aplikaci byste měli uložit připojovací řetězec bezpečně, jak je popsáno v [připojovací řetězce a konfigurační soubory](http://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8).  
  
##  <a name="BKMK_retrievetheconnectionstring"></a> Načtení připojovacího řetězce  
  
1.  Na panelu nabídek vyberte **projektu** > **přidat odkaz**a pak přidejte odkaz na System.Configuration.dll.  
  
2.  Na panelu nabídek vyberte **projektu** > **přidat třídu** přidejte soubor třídy do projektu a potom zadejte název souboru `Utility`.  
  
     Visual Studio vytvoří soubor a zobrazí ho v **Průzkumníka řešení**.  
  
3.  V souboru s nástroji nahraďte kód zástupce následujícím kódem. Všimněte si číslovaných komentářů (s předponou Util.-), které identifikují oddíly kódu. Tabulka, která následuje kód, volá klíčové body.  
  
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
    |Util.-1|Přidat `System.Configuration` oboru názvů.|  
    |Util.-2|Definujte proměnnou, `returnValue`a inicializujte ji na `null` (C#) nebo `Nothing` (Visual Basic).|  
    |Util.-3|I když jste zadali `connString` jako název připojovacího řetězce v **vlastnosti** okna, je nutné zadat `"SimpleDataApp.Properties.Settings.connString"` (C#) nebo `"SimpleDataApp.My.MySettings.connString"` (Visual Basic) v kódu.|  
  
##  <a name="BKMK_writethecodefortheforms"></a> Napište kód pro formuláře  
 Tato část obsahuje stručný přehled, co každá forma provádí a zobrazuje kód, který vytváří formy. Očíslované poznámky určují oddíly kódu.  
  
### <a name="navigation-form"></a>Navigační formulář  
 Navigační formulář se otevře při spuštění aplikace. **Přidat účet** tlačítko k otevření formuláře NewCustomer. **Vyplnit nebo zrušit objednávku** tlačítko k otevření formuláře FillOrCancel. **Ukončovací** tlačítko slouží k ukončení aplikace.  
  
#### <a name="make-the-navigation-form-the-startup-form"></a>Vytvořit formulář změna formuláře úvodního formuláře navigace  
 Pokud používáte C#, v **Průzkumníku řešení**, otevřete soubor Program.cs a potom změňte `Application.Run` řádek, který toto: `Application.Run(new Navigation());`  
  
 Pokud používáte Visual Basic v **Průzkumníka řešení**, otevřete **vlastnosti** okna, vyberte **aplikace** kartu a potom vyberte  **SimpleDataApp.Navigation** v **úvodní formulář** seznamu.  
  
#### <a name="create-event-handlers"></a>Vytváření obslužných rutin událostí  
 Dvakrát klikněte na tři tlačítka na formuláři, chcete-li vytvořit prázdné obslužné rutiny události metod.  
  
#### <a name="create-code-for-navigation"></a>Vytvořit kód pro Navigation  
 Ve formuláři navigace nahraďte stávající kód následujícím kódem.  
  
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
 Když zadáte název zákazníka a pak vyberete **vytvořit účet** tlačítko, formulář NewCustomer vytvoří účet zákazníka a SQL Server vrátí hodnotu IDENTITY jako nové číslo účtu. Poté pošlete objednávku nového účtu zadáním částku a data objednávky a výběrem **objednat** tlačítko.  
  
#### <a name="create-event-handlers"></a>Vytváření obslužných rutin událostí  
 Vytvořit prázdný klikněte na obslužnou rutinu události pro každé tlačítko na formuláři.  
  
#### <a name="create-code-for-newcustomer"></a>Vytvořit kód pro NewCustomer  
 Do formuláře NewCustomer přidejte následující kód. Projděte skrze každý blok kódu pomocí číslovaných komentářů a tabulky uvedené za kódem.  
  
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
|NC-1|Přidat `System.Data.SqlClient` a `System.Configuration` do seznamu oborů názvů.|  
|NC-2|Deklarovat `parsedCustomerID` a `orderID` proměnné, které budete potřebovat později.|  
|NC-3|Volání `GetConnectionString` metodu k získání připojovacího řetězce z konfiguračního souboru aplikace a uložte hodnotu `connstr` proměnné řetězce.|  
|NC-4|Přidejte kód pro obslužnou rutinu události kliknutí `btnCreateAccount` tlačítko.|  
|NC-5|Zabalte volání do `isCustomerName` okolo kódu události Click tak, aby `uspNewCustomer` spustí pouze v případě, že je k dispozici název zákazníka.|  
|NC 6|Vytvoření `SqlConnection` objektu (`conn`) a předejte mu připojovací řetězec v `connstr`.|  
|NC-7|Vytvoření `SqlCommand` objektu, `cmdNewCustomer`.<br /><br /> -Zadat `Sales.uspNewCustomer` jako uloženou proceduru pro spuštění.<br />– Použijte `CommandType` vlastnosti a určit tak, že příkaz je uložená procedura.|  
|NC-8|Přidat `@CustomerName` vstupní parametr z uložené procedury.<br /><br /> -Přidat parametr `Parameters` kolekce.<br />– Použijte `SqlDbType` výčet k určení typu parametru jako nvarchar(40).<br />-Zadat `txtCustomerName.Text` jako zdroj.|  
|NC-9|Přidejte výstupní parametr z uložené procedury.<br /><br /> -Přidat parametr `Parameters` kolekce.<br />– Použijte `ParameterDirection.Output` k identifikaci parametru jako výstupního.|  
|NC-10|Přidáte blok konstrukce Try-Catch-Finally k otevření připojení, spuštění uložené procedury, zpracování výjimek a nakonec k ukončení připojení.|  
|NC-11|Otevřete připojení (`conn`), který jste vytvořili v rámci NC 6.|  
|NC-12|Použití `ExecuteNonQuery` metodu `cmdNewCustomer` ke spuštění `Sales.uspNewCustomer` uložené procedury. To uložená procedura spuštění `INSERT` příkaz, nikoli dotaz.|  
|NC-13|`@CustomerID` Je vrácena jako hodnota IDENTITY z databáze. Protože jde o celé číslo, bude nutné ji převést na řetězec pro zobrazení v **ID zákazníka** textového pole.<br /><br /> -Můžete deklarovat `parsedCustomerID` v NC-2.<br />-Store `@CustomerID` hodnota v `parsedCustomerID` pro pozdější použití.<br />-Převeďte vrácené ID zákazníka na řetězec a vložte jej do `txtCustomerID.Text`.|  
|NC-14|V tomto příkladu přidejte jednoduchou klauzuli catch (ne produkční kvality).|  
|NC-15|Vždy uzavírejte připojení po dokončení jeho použití, tak, aby mohlo být uvolněno do fondu připojení. Zobrazit [připojení k SQL serveru (ADO.NET) sdružování](http://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|  
|NC-16|Definujte metodu k ověření, že je k dispozici název zákazníka.<br /><br /> – Pokud textové pole je prázdné, zobrazí zprávu a vrátí `false`, protože název se vyžaduje k vytvoření účtu.<br />-Pokud textové pole není prázdný, vrátí `true`.|  
|NC-17|Přidejte kód pro obslužnou rutinu události kliknutí `btnPlaceOrder` tlačítko.|  
|NC-18|Zabalte volání do `isPlaceOrderReady` kolem `btnPlaceOrder_Click` kód události tak, aby `uspPlaceNewOrder` nespustil, pokud požadovaný vstup není přítomen.|  
|NC-19 až NC 25|Tyto části kódu se podobají kódu, který jste přidali pro `btnCreateAccount_Click` obslužné rutiny události.<br /><br /> -NC-19. Vytvořte `SqlCommand` objektu, `cmdNewOrder`a určete `Sales.uspPlaceOrder` jako uloženou proceduru.<br />-NC-20 až NC 23 jsou vstupní parametry pro uloženou proceduru.<br />NC-24. `@RC` bude obsahovat vrácenou hodnotu, která je vygenerovaným ID objednávky z databáze. Směr tohoto parametru je zadán jako `ReturnValue`.<br />NC 25. Hodnotu ID objednávky v Store `orderID` proměnné, která je deklarována v rámci NC-2 a hodnotu zobrazte v okně se zprávou.|  
|NC-26|Definujte metodu k ověření, že ID zákazníka existuje a že dobu, jakou se v zadané `numOrderAmount`.|  
|27. SÍŤOVÝ ADAPTÉR.|Volání `ClearForm` metodu `btnAddAnotherAccount` obslužné rutiny kliknutí.|  
|NC-28|Vytvořte `ClearForm` metodu pro mazání hodnot z formuláře, pokud chcete přidat dalšího zákazníka.|  
|NC29|Zavřete formulář NewCustomer a vraťte se do navigačního formuláře.|  
  
### <a name="fillorcancel-form"></a>Formulář FillOrCancel  
 Formulář FillorCancel spustí dotaz a vrátit objednávku, když zadejte ID objednávky a vyberte **vyhledat objednávku** tlačítko. Vrácený řádek se zobrazí v mřížce dat jen pro čtení. Můžete označit objednávku jako zrušenou (X), pokud jste vybrali **zrušit objednávku** tlačítko, nebo můžete označit objednávku jako vyplněnou (F) Pokud jste vybrali **vyplnit objednávku** tlačítko. Pokud vyberete **vyhledat objednávku** tlačítko znovu, zobrazí se aktualizovaný řádek.  
  
#### <a name="create-event-handlers"></a>Vytváření obslužných rutin událostí  
 Vytvořit prázdné obslužné rutiny událostí pro čtyři tlačítka na formuláři klikněte na tlačítko.  
  
#### <a name="create-code-for-fillorcancel"></a>Vytvořit kód pro FillOrCancel  
 Do formuláře FillOrCancel přidejte následující kód. Projděte skrze všechny bloky kódu pomocí číslovaných komentářů a tabulky uvedené za kódem.  
  
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
|FC-1|Přidat `System.Data.SqlClient`, `System.Configuration`, a `System.Text.RegularExpressions` do seznamu oborů názvů.|  
|FC-2|Deklarovat `parsedOrderID` proměnné.|  
|FC-3|Volání `GetConnectionString` metodu k získání připojovacího řetězce z konfiguračního souboru aplikace a uložte hodnotu `connstr` proměnné řetězce.|  
|FC-4|Přidejte kód do obslužné rutiny události kliknutí pro `btnFindOrderByID`.|  
|FC-5|Tyto kroky je třeba před pokusem o spuštění příkazu SQL nebo uloženou proceduru.<br /><br /> – Vytváření `SqlConnection` objektu.<br />-Definujte příkaz SQL nebo zadejte název uložené procedury. (V tomto případě je potřeba spustit `SELECT` příkazu.)<br />– Vytváření `SqlCommand` objektu.<br />-Definujte libovolné parametry pro příkaz SQL nebo uloženou proceduru.|  
|FC-6|Tento kód používá `SqlDataReader` a `DataTable` k načtení a zobrazení výsledku dotazu.<br /><br /> -Otevření připojení.<br />– Vytváření `SqlDataReader` objektu, `rdr`, spuštěním `ExecuteReader` metodu `cmdOrderID`.<br />– Vytváření `DataTable` objekt pro uložení načtených data.<br />-Načtení dat z `SqlDataReader` objektu do `DataTable` objektu.<br />– Zobrazení dat v zobrazení mřížky dat tak, že zadáte `DataTable` jako `DataSource` pro zobrazení mřížky dat.<br />– Zavřete `SqlDataReader`.|  
|FC-7|Přidejte kód do obslužné rutiny události kliknutí pro `btnCancelOrder`. Tento kód se spustí `Sales.uspCancelOrder` uložené procedury.|  
|FC-8|Přidejte kód do obslužné rutiny události kliknutí pro `btnFillOrder`. Tento kód se spustí `Sales.uspFillOrder` uložené procedury.|  
|FC-9|Vytvořit metodu pro ověření, že `OrderID` je připraveno odeslat jako parametr `SqlCommand` objektu.<br /><br /> – Ujistěte se, že bylo zadáno ID v `txtOrderID`.<br />– Použijte `Regex.IsMatch` k definování jednoduchého vyhledání znaků jiných než celých čísel.<br />-Je deklarován `parsedOrderID` proměnné na FC-2.<br />– Pokud je vstup platný, převede text na celé číslo a uložte hodnotu `parsedOrderID` proměnné.<br />-Zabalení `isOrderID` metoda kolem `btnFindByOrderID`, `btnCancelOrder`, a `btnFillOrder` obslužné rutiny události kliknutí.|  
  
##  <a name="BKMK_testyourapplication"></a> Testování aplikace  
 Vyberte klávesu F5 k sestavení a testování vaší aplikace po kódu každé obslužné rutiny události kliknutí a potom můžete po dokončení kódování.

