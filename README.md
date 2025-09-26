# krishna-


//Logout code :-

static Future<void> _confirmAndLogout(BuildContext context) async {
    final shouldLogout = await showDialog<bool>(
      context: context,
      builder: (ctx) {
        return AlertDialog(
          title: const Text('Logout'),
          content: const Text("Log out of your account?"),
          actions: [
            TextButton(
              onPressed: () => Navigator.of(ctx).pop(false),
              child: const Text("Cancel"),
            ),
            TextButton(
              onPressed: () => Navigator.of(ctx).pop(true),
              child: const Text("Logout"),
            ),
          ],
        );
      },
    );

    if (shouldLogout == true) {
     
      if (Navigator.of(context).canPop()) {
        Navigator.of(context).pop();
      }
      await AuthStorageHelper.clearLoginData();
      if (context.mounted) {
        context.go(AppRoutes.login);
      }
    }
  }
}                                        //Call them:- drawerItem(
            Icons.logout,
            "Logout",
            onTap: () => _confirmAndLogout(context),
          ),
