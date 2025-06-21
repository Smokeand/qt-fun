//章鱼记账
package com.example.Atrosenet;

import de.robv.android.xposed.IXposedHookLoadPackage;
import de.robv.android.xposed.XC_MethodReplacement;
import de.robv.android.xposed.XposedHelpers;
import de.robv.android.xposed.callbacks.XC_LoadPackage.LoadPackageParam;

public class cashbook implements IXposedHookLoadPackage {

	@Override
	public void handleLoadPackage(LoadPackageParam lpparam) throws Throwable {
		if ("com.shengjue.cashbook".equals(lpparam.packageName)) {
			XposedHelpers.findAndHookMethod(
				"com.hjq.demo.entity.VipCardInfoData", //类名
				lpparam.classLoader,
				"getExpireStatus", //方法名
				XC_MethodReplacement.returnConstant(3));
			XposedHelpers.findAndHookMethod(
				"com.hjq.demo.entity.VipCardInfoData", //类名
				lpparam.classLoader,
				"getExpireTime", //方法名
				XC_MethodReplacement.returnConstant(1956542400));
				
		}

	}

}
