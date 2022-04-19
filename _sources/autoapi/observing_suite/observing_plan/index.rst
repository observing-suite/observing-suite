:py:mod:`observing_suite.observing_plan`
========================================

.. py:module:: observing_suite.observing_plan


Module Contents
---------------

Classes
~~~~~~~

.. autoapisummary::

   observing_suite.observing_plan.ObservingPlan




.. py:class:: ObservingPlan(target_list: list, observatory: str, obsdates: list, utcoffset: float)

   .. py:method:: plot_visibility(self, date: str, target: str = 'all', view_range: float = 12, plot_current_time: bool = False, figsize: tuple = (30, 12), alt_min: float = 10, alt_max: float = 90)

      Produce a plot of altitude and airmass for targets on a given night of observing.

      :param date: date on which to make the plot. In form 'YYYY-MM-DD'. Must be a date specified within obsdate.
      :type date: str
      :param target: target to plot track for. deault is "all". Individual targets can be specified by name (str), via a list or, for single objects, a str.
      :type target: str or list, optional (default 'all')
      :param view_range: number of hours on either side of midnight over which to show the plot
      :type view_range: int, optional, default 12
      :param plot_current_time: show a vertical bar at the current time (when code executed). Useful when making plot interactively during a night.
      :type plot_current_time: bool, optional (default False)
      :param figsize: tuple specifying the figure size
      :type figsize: tuple, optional (default (15,12))


   .. py:method:: export_targetlist(self, include_extras: list = [], include_offset_stars: bool = True, save_path: str = './', name: str = 'targetlist')

      Export an observatory-compliant targetlist of all targets and configurations.
      If only one configuration exists, the name column will be the target name.
      Otherwise, it will be targetname_configname. It's worth noting that keeping
      both of these short is advantageous for many facsum ingesting tools.
      By default, only key info (name,ra,dec,equinox) are added. Extra info
      from the configs can be added and will be appended as commented lines
      below each row.

      :param include_extras: extra keywords to include in comments. Code will try to add them if they
                             exist for a given configuration. (e.g., PAs or offsets)
      :type include_extras: list, default: []
      :param include_offset_stars: whether to include offset stars as entries in the targetlist. Name format is <target>_<config>_os.
      :type include_offset_stars: bool, default: True
      :param save_path: path to save targetlist to. default is current directory.
      :type save_path: str, default: './'
      :param name: name of the file.
      :type name: str, default: 'targetlist'

      :returns: but saves the relevant targetlist file.
      :rtype: None

      .. rubric:: Notes

      CURRENT_SUPPORTED_OBS: Palomar Observatory


   .. py:method:: html_summary(self, date: str, save_dir: str, overwrite: bool = True, view_range: float = 12)

      Produce a 'beautiful' html output with the observing plan.

      :param date: date for which to construct the report. Must be a date present in the obsdates provided.
      :type date: str
      :param save_dir: location to save the observing plan. Spawns an image directory for relevant plots.
      :type save_dir: str
      :param overwrite: When set to true, constituant elements (like finder charts, airmass plots, etc) will be re-computed and saved to disk.
      :type overwrite: bool, optional (default True)



