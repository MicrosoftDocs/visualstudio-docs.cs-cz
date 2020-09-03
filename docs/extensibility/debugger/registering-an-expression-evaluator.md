---
title: Registrace vyhodnocovacího filtru výrazů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713200"
---
# <a name="register-an-expression-evaluator"></a>Registrace vyhodnocovacího filtru výrazů
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Vyhodnocovací filtr výrazů (EE) se musí zaregistrovat jako objekt pro vytváření tříd pomocí prostředí Windows COM a sady Visual Studio. EE je nastaven jako knihovna DLL tak, aby byla vložena do adresního prostoru ladicího stroje (DE) nebo do adresního prostoru sady Visual Studio v závislosti na tom, která entita vytváří instanci EE.

## <a name="managed-code-expression-evaluator"></a>Filtr výrazů spravovaného kódu
 Spravovaný kód EE je implementován jako knihovna tříd, což je knihovna DLL, která se zaregistruje do prostředí COM, obvykle spouštěná voláním programu VSIP, *regpkg.exe*. Vlastní proces psaní klíčů registru pro prostředí COM se zpracovává automaticky.

 Metoda hlavní třídy je označena atributem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> , který označuje, že metoda bude volána při registraci knihovny DLL v modelu COM. Tato metoda registrace často volá `RegisterClass` úlohu registrace knihovny DLL se sadou Visual Studio. Odpovídající objekt `UnregisterClass` (označený jako <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> ), vrátí důsledky `RegisterClass` při odinstalaci knihovny DLL.
Stejné položky registru jsou vytvořeny jako pro EE napsané v nespravovaném kódu; Jediným rozdílem je, že není k dispozici žádná pomocná funkce, například `SetEEMetric` k tomu, aby fungovala za vás. Následuje příklad procesu registrace a zrušení registrace.

### <a name="example"></a>Příklad
 Následující funkce ukazuje, jak spravovaný kód EE registruje a odregistruje se v aplikaci Visual Studio.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        #region Register and unregister.
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");
        private static string languageName = "MyC";
        private static string eeName = "MyC Expression Evaluator";

        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");

        /// <summary>
        /// Register the expression evaluator.
        /// Set "project properties/configuration properties/build/register for COM interop" to true.
        /// </summary>
         [ComRegisterFunctionAttribute]
        public static void RegisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator";

            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);
            if (rk == null)  return;

            rk = rk.CreateSubKey(guidMycLang.ToString("B"));
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));
            rk.SetValue("CLSID", t.GUID.ToString("B"));
            rk.SetValue("Language", languageName);
            rk.SetValue("Name", eeName);

            rk = rk.CreateSubKey("Engine");
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));
        }
        /// <summary>
        /// Unregister the expression evaluator.
        /// </summary>
         [ComUnregisterFunctionAttribute]
        public static void UnregisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator\"
                        + guidMycLang.ToString("B");
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);
            if (key != null)
            {
                key.Close();
                Registry.LocalMachine.DeleteSubKeyTree(s);
            }
        }
    }
}
```

## <a name="unmanaged-code-expression-evaluator"></a>Vyhodnocení výrazu nespravovaného kódu
 Knihovna EE DLL implementuje `DllRegisterServer` funkci pro registraci k prostředí com i k aplikaci Visual Studio.

> [!NOTE]
> Můžete najít ukázkový kód registru MyCEE v souboru *dllentry. cpp*, který se nachází v instalaci VSIP v části EnVSDK\MyCPkgs\MyCEE.

### <a name="dll-server-process"></a>Proces serveru DLL
 Při registraci EE se jedná o server knihovny DLL:

1. Registruje svůj objekt `CLSID` pro vytváření tříd podle normálních konvencí modelu COM.

2. Volá pomocnou funkci `SetEEMetric` pro registraci v aplikaci Visual Studio metrika EE uvedená v následující tabulce. Funkce `SetEEMetric` a metriky, které jsou zadány takto, jsou součástí knihovny *dbgmetric. lib* . Podrobnosti najdete v tématech [pomocníka sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) .

    |Metrika|Popis|
    |------------|-----------------|
    |`metricCLSID`|`CLSID` třídy et – objekt pro vytváření tříd|
    |`metricName`|Název EE jako zobrazitelný řetězec|
    |`metricLanguage`|Název jazyka, který má být k vyhodnocení v EE navržený|
    |`metricEngine`|`GUID`s moduly ladění (DE), které pracují s tímto EE|

    > [!NOTE]
    > `metricLanguage``GUID`Určuje jazyk podle názvu, ale je to `guidLang` argument pro `SetEEMetric` Výběr jazyka. Když kompilátor vygeneruje soubor s informacemi o ladění, měl by napsat vhodné, `guidLang` aby příkaz de ví, který se má použít. Verze DE obvykle žádá poskytovatele symbolů pro tento jazyk `GUID` , který je uložen v ladicím souboru s informacemi.

3. Zaregistrujte se sadou Visual Studio tak, že vytvoříte klíče pod HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *X. y*, kde *X. y* je verze sady Visual Studio, ve které se má zaregistrovat.

### <a name="example"></a>Příklad
 Následující funkce ukazuje, jak nespravovaný kód (C++) EE registruje a ruší registraci v aplikaci Visual Studio.

```cpp
/*---------------------------------------------------------
  Registration
-----------------------------------------------------------*/
#ifndef LREGKEY_VISUALSTUDIOROOT
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"
#endif

static HRESULT RegisterMetric( bool registerIt )
{
    // check where we should register
    const ULONG cchBuffer = _MAX_PATH;
    WCHAR wszRegistrationRoot[cchBuffer];
    DWORD cchFreeBuffer = cchBuffer - 1;
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);
    wcscat(wszRegistrationRoot, L"\\");

    // this is Environment SDK specific
    // we check for  EnvSdk_RegKey environment variable to
    // determine where to register
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;
    DWORD cchEnvVarRead = GetEnvironmentVariableW(
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value
        /* DWORD   */ cchFreeBuffer);// size of buffer
    if (cchEnvVarRead >= cchFreeBuffer)
        return E_UNEXPECTED;
    // If the environment variable does not exist then we must use
    // LREGKEY_VISUALSTUDIOROOT which has the version number.
    if (0 == cchEnvVarRead)
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);

    if (registerIt)
    {
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricCLSID,
                    CLSID_MycEE,
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricName,
                    GetString(IDS_INFO_MYCDESCRIPTION),
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricLanguage, L"MyC",
                    wszRegistrationRoot);

        GUID engineGuids[2];
        engineGuids[0] = guidCOMPlusOnlyEng;
        engineGuids[1] = guidCOMPlusNativeEng;
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricEngine,
                    engineGuids,
                    2,
                    wszRegistrationRoot);
    }
    else
    {
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricCLSID,
                        wszRegistrationRoot);
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricName,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricLanguage,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricEngine,
                        wszRegistrationRoot );
    }

    return S_OK;
}
```

## <a name="see-also"></a>Viz také
- [Zápis vyhodnocovacího filtru výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Pomocníka sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
