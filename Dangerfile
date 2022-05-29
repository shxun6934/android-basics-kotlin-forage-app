# # Sometimes it's a README fix, or something like that - which isn't relevant for
# # including in a project's CHANGELOG for example
# declared_trivial = github.pr_title.include? "#trivial"
#
# # Make it more obvious that a PR is a work in progress and shouldn't be merged yet
# warn("PR is classed as Work in Progress") if github.pr_title.include? "[WIP]"
#
# # Warn when there is a big PR
# warn("Big PR") if git.lines_of_code > 500
#
# # Don't let testing shortcuts get into master by accident
# fail("fdescribe left in tests") if `grep -r fdescribe specs/ `.length > 1
# fail("fit left in tests") if `grep -r fit specs/ `.length > 1

# 変更した行以外は指摘しないように
github.dismiss_out_of_range_messages

# ktlint
checkstyle_format.base_path = Dir.pwd
Dir["*/build/reports/ktlint/ktlint-result.xml"].each do |file|
  checkstyle_format.report file
end

# android lint
android_lint.skip_gradle_task = true
android_lint.filtering = true
Dir["*/build/reports/lint-results*.xml"].each do |file|
  android_lint.report_file = file
  android_lint.lint(inline_mode: true)
end
